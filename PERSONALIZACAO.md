# SparkyFitness — Documentação do Self-Host (personalização)

> Registro operacional da instância self-hosted (fork `harissonford/SparkyFitness`).
> Não faz parte do upstream — arquivo local do dono da instância.
> **Última atualização: 2026-08-11.**

---

## 1. Como este ambiente roda

- **É build local.** As imagens do app são **construídas aqui** a partir do código-fonte já sincronizado (§3)
  e apenas *carregam os nomes* das imagens do Docker Hub, que estão congeladas desde ~2026-07-06:
  - `codewithcj/sparkyfitness:latest` (frontend) — build local
  - `codewithcj/sparkyfitness_server:latest` (servidor) — build local
  - `postgres:18.3-alpine` (banco) — esta sim vem pronta do Docker Hub
- Orquestração via Docker Compose, **projeto `docker`**, com dois arquivos:
  ```
  docker/docker-compose.prod.yml + docker/docker-compose.local.yml
  ```
- Portas: frontend `3004`, servidor `3010`, Postgres exposto só em `127.0.0.1:5432` (ver §5).

### Containers
| Container | Imagem | Papel |
|---|---|---|
| `docker-sparkyfitness-frontend-1` | `codewithcj/sparkyfitness:latest` | Web (React/Vite/nginx) |
| `docker-sparkyfitness-server-1` | `codewithcj/sparkyfitness_server:latest` | API Express + migrations |
| `sparkyfitness-db` | `postgres:18.3-alpine` | Banco |

### Volumes nomeados (dados persistentes — **não apagar**)
- `docker_sparky_pg` → dados do Postgres
- `docker_sparky_uploads` → uploads
- `docker_sparky_backup` → backups internos do app

### Banco / identidade
- DB `sparkyfitness_db`, user `sparky`.
- Criptografia de segredos de provedores: `SPARKY_FITNESS_API_ENCRYPTION_KEY` (AES-256-GCM).
- Migrations são aplicadas **automaticamente no boot do servidor**; RLS (Row-Level Security) é reaplicado a cada start.
- **Importante:** atualizar o *código-fonte* (git) **não** muda o app rodando. O app só muda quando você **rebuilda as imagens localmente** e recria os containers (ver §3).

---

## 2. Git — fork e branches

- `origin` = fork pessoal `github.com/harissonford/SparkyFitness`
- `upstream` = `github.com/CodeWithCJ/SparkyFitness`
- Branches:
  - `main` — espelha `upstream/main` (não editar; só fast-forward).
  - `personalizacao` — branch de trabalho. = `upstream/main` + **commits próprios de docs** (`PERSONALIZACAO.md`, `RELATORIO_SEED_REFEICOES.md`) por cima + ajustes locais não commitados (ver §5).

> ⚠️ Como a `personalizacao` **tem commits próprios**, ela **NÃO é mais fast-forward** do upstream. Use **`git rebase upstream/main`** (mantém os commits de docs no topo, linear) — `git merge --ff-only` vai falhar. Após rebase, o push precisa de `--force-with-lease` (a history foi reescrita).

### Atualizar o git com o upstream (sem perder personalização)
```bash
git fetch upstream --prune

# guarda ajustes locais não commitados (bind 127.0.0.1)
git stash push -m "ajustes locais" docker/docker-compose.dev.yml docker/docker-compose.db_dev.yml

# rebase a branch de trabalho sobre o upstream (replaya os commits de docs no topo)
git checkout personalizacao
git rebase upstream/main

# reaplica os ajustes locais
git stash pop

# espelha main (fast-forward puro) e envia tudo ao fork
git branch -f main upstream/main
git push --force-with-lease origin personalizacao
git push origin main
```
> Se o `stash pop` conflitar: os ajustes locais são só a linha da porta do Postgres — resolver mantendo `"127.0.0.1:5432:5432"`.
> Se o `rebase` conflitar: preferir o upstream no código e manter os arquivos de docs; se ficar ambíguo, `git rebase --abort` e revisar manualmente.
> O diretório `ha/` (toolkit de alta disponibilidade) fica **untracked** — não commitar, e nunca commitar `ha/node.env` (tem segredo).

---

## 3. Atualizar o APP (imagens + migrations) — runbook

> **Sempre faça backup antes (§4).** As migrations são aditivas, mas backup é obrigatório.

> 🚫 **NUNCA rode `docker compose pull` neste deploy.** O upstream **parou de republicar as imagens no Docker Hub** (`codewithcj/*:latest` congeladas desde ~2026-07-06). Um `pull` **sobrescreveria as imagens que buildamos localmente com versões antigas = downgrade** em cima dos seus dados. A atualização aqui é **build local** a partir do código já sincronizado (§2).

```bash
cd /Volumes/FORD_2TB/claudeAI/projetos/SparkyFitness
C="-p docker -f docker/docker-compose.prod.yml -f docker/docker-compose.local.yml"
TS=$(date +%Y%m%d)

# 1. Backup do banco (ver §4) — OBRIGATÓRIO

# 2. Marca as imagens atuais como rollback (pra voltar rápido se algo quebrar)
docker tag codewithcj/sparkyfitness_server:latest codewithcj/sparkyfitness_server:rollback-$TS
docker tag codewithcj/sparkyfitness:latest        codewithcj/sparkyfitness:rollback-$TS

# 3. Build LOCAL das imagens (BuildKit é obrigatório — os Dockerfiles usam --platform=$BUILDPLATFORM)
DOCKER_BUILDKIT=1 docker build -f docker/Dockerfile.backend  -t codewithcj/sparkyfitness_server:latest .
DOCKER_BUILDKIT=1 docker build -f docker/Dockerfile.frontend -t codewithcj/sparkyfitness:latest .

# 4. Recria containers (o DB não é recriado; server aplica migrations no boot). SEM --pull, SEM --build de dev.
docker compose $C up -d

# 5. Acompanha as migrations
docker logs docker-sparkyfitness-server-1 2>&1 | grep -iE "migrat|RLS|listening"

# 6. Verifica saúde + confirma que roda as imagens novas (não as antigas do Hub)
docker ps --filter name=sparky --format 'table {{.Names}}\t{{.Status}}'
curl -sf http://localhost:3004/api/health   # => {"status":"UP"}
```

> **Pré-requisito de build:** o plugin `docker-buildx` (instalado via `brew install docker-buildx`, com symlink em `~/.docker/cli-plugins/docker-buildx`). Sem ele, o build falha com `BuildKit is enabled but the buildx component is missing`.

### Rollback (se o update quebrar)
```bash
docker tag codewithcj/sparkyfitness_server:rollback-$TS codewithcj/sparkyfitness_server:latest
docker tag codewithcj/sparkyfitness:rollback-$TS        codewithcj/sparkyfitness:latest
docker compose $C up -d
# se necessário, restaurar o banco pelo dump do §4
```

### Quando atualizar
O gatilho é **avanço do git upstream** (§2), não "imagem nova no Hub" (que não sai mais). Depois de `git rebase upstream/main`, rebuilde local com os passos acima. Para ver quanto o upstream andou:
```bash
git fetch upstream && git rev-list --count HEAD..upstream/main   # nº de commits atrás
```
Há também um script de aviso automático: `/Volumes/FORD_2TB/claudeAI/scripts/sparky-auto-update.sh`
com **cron diário às 9h em modo `--check`** (só notifica, não atualiza sozinho).

---

## 4. Backup e restauração do banco

### Backup (fazer antes de qualquer update)
```bash
TS=$(date +%Y%m%d_%H%M%S)
BK=/Volumes/FORD_2TB/claudeAI/backups/SparkyFitness_${TS}
mkdir -p "$BK"
docker exec sparkyfitness-db pg_dump -U sparky -d sparkyfitness_db -Fc  > "$BK/db_sparkyfitness.dump"     # custom
docker exec sparkyfitness-db pg_dump -U sparky -d sparkyfitness_db | gzip > "$BK/db_sparkyfitness.sql.gz" # texto
```
Backups ficam em `/Volumes/FORD_2TB/claudeAI/backups/SparkyFitness_*`.

### Restaurar (emergência)
```bash
gunzip -c "$BK/db_sparkyfitness.sql.gz" | docker exec -i sparkyfitness-db psql -U sparky -d sparkyfitness_db
```

---

## 5. Ajustes locais (personalização) mantidos fora do upstream

1. **Postgres exposto só em localhost** — em `docker/docker-compose.dev.yml` e
   `docker/docker-compose.db_dev.yml` a porta é `"127.0.0.1:5432:5432"` (upstream usa `"5432:5432"`).
   *Motivo:* segurança — não expor o banco na rede. Mantido **não commitado** de propósito.

2. **Provedores de comida configurados** (ver §6).

3. **Seed de dados brasileiros** (ver §7) — dados no banco, não em arquivo de código.

---

## 6. Provedores externos ativos

| Provedor | Tipo | Observação |
|---|---|---|
| **Open Food Facts** | `openfoodfacts` | Open data (ODbL) — pode importar/bulk-copiar. |
| **FatSecret** | `fatsecret` | **Padrão de comida.** Credenciais criptografadas (AES-256-GCM). IP liberado no painel. **NÃO fazer bulk-copy** (termos da API — usar só on-demand). |
| Free Exercise DB | `free-exercise-db` | Exercícios. |
| Swiss Food Database | `swissfood` | Comida. |
| Wger | `wger` | Exercícios. |

> Segredos do FatSecret vivem **criptografados** nas colunas `encrypted_app_id/iv/tag` e
> `encrypted_app_key/iv/tag` da tabela `external_data_providers`. Nunca em texto puro.

---

## 7. Seed de dados brasileiros (feito manualmente)

Inserido via SQL direto (replicando a lógica do app), **não** via upstream:

- **+119 alimentos** (de 602 → 721): variante base por 100 g cada.
  - `provider_type='taco'` → valores aproximados da Tabela TACO.
  - `provider_type='openfoodfacts'` → dados reais do Open Food Facts Brasil.
- **+100 refeições** compostas (`meals` + `meal_foods`), categorias
  `Café da manhã / Lanche / Almoço / Almoço reforçado / Jantar` + pratos especiais.
- Relatório detalhado (ingredientes, gramas e macros de cada refeição):
  **[`RELATORIO_SEED_REFEICOES.md`](./RELATORIO_SEED_REFEICOES.md)**.

### Pendência conhecida
Alguns pratos são **1 alimento agregado por 100 g**, não decompostos em ingredientes:
Misto quente, Feijoada, Coxinha, Pastel, Strogonoff. Para transformá-los em receitas
compostas de verdade (ex.: misto quente = 2 fatias pão de forma + mussarela + presunto),
falta primeiro cadastrar ingredientes ausentes (ex.: "presunto").

---

## 9. Auto-start após reboot

O Docker aqui é **Colima** (VM `odysseus`) e **não sobe sozinho** após reiniciar; o **Tailscale** também não reconectava. Configurado em 2026-07-11:

1. **Colima** — LaunchAgent `~/Library/LaunchAgents/com.harisson.sparkyfitness-colima.plist`
   (`RunAtLoad`) chama o wrapper `~/.sparkyfitness/start-colima-odysseus.sh`; logs em
   `~/.sparkyfitness/colima-launchd.*.log` (launchd) e `~/.sparkyfitness/colima-start.log` (wrapper).
   Os containers sparky sobem sozinhos junto (têm restart policy). Arquivos ficam no HOME de propósito
   (o disco externo pode não estar montado no login).

   **Por que um wrapper e não `colima start` direto (diag 2026-07-14):** com o driver
   **Apple Virtualization (`vz`)**, o `RunAtLoad` dispara cedo demais no login e a VM aborta em ~2 s
   (`error starting vm: exit status 1`). Rodando manualmente minutos depois, sempre funciona.
   O wrapper resolve isso: `sleep 25` (deixa a sessão assentar) + sai se já estiver Running +
   **retry 3×** com `colima stop --force` entre as tentativas.

   ⚠️ **Contexto docker global:** existem vários perfis Colima na máquina (`1wa26ai`, `default`, etc.).
   O contexto docker é global e pode ser trocado por outro perfil/sessão, fazendo `docker ps` parecer vazio.
   Se acontecer, o app **não** caiu — é só reapontar: `docker context use colima-odysseus`.
2. **Tailscale** — adicionado aos **Login Items** do macOS (`System Events`). Ao logar, o app abre e reconecta
   (mantém o mesmo IP `100.90.75.18` / nome `harisson-mac-m4.taila82c6e.ts.net`).

### Se após um reboot o app não responder, checar nesta ordem
```bash
colima list | grep odysseus                 # a VM 'odysseus' está Running?
colima start odysseus                        # se Stopped
docker ps --filter name=sparky               # 3 containers healthy?
/Applications/Tailscale.app/Contents/MacOS/Tailscale status | head -1   # tailscale up?
```
> ⚠️ Após reboot o IP da **LAN de casa muda** conforme a rede (ex.: no hotspot do iPhone vira `172.20.10.x`).
> O acesso estável é sempre pelo **nome Tailscale**: `http://harisson-mac-m4.taila82c6e.ts.net:3004`.

## 8. Histórico de atualizações

### 2026-08-11 — Sincronizado com o upstream **pós-v1.6.1** (build local); 1ª migration nova desde julho
- `main` `22415819` → `77a93080`; `personalizacao` = `77a93080` + os 3 commits de docs recolocados por cima
  (os 2 antigos + este registro). **27 commits** do upstream.
  **Ainda não há release nova**: o `package.json` continua em `1.6.1` e nenhuma tag aponta para `77a93080` —
  é o estado de desenvolvimento depois da v1.6.1, não uma v1.6.2.
- Rebase **sem nenhum conflito** (meus 3 commits só tocam `PERSONALIZACAO.md` e `RELATORIO_SEED_REFEICOES.md`).
  Os ajustes de `127.0.0.1:5432` foram guardados com `git stash` e recolocados limpos — o upstream não mexeu em `docker/`.
- ⚠️ **Uma migration nova** (`20260807000000_add_record_timezone_to_sleep_entries.sql`) — diferente das últimas vezes,
  desta vez o banco *foi* alterado. É puramente aditiva: duas colunas nulas (`record_timezone`,
  `record_utc_offset_minutes`) com `IF NOT EXISTS`; linhas antigas continuam renderizando igual. Aplicada com sucesso
  no boot, confirmada em `information_schema`.
- Backup pré-update: `~/.sparkyfitness/backups/pre-upstream-20260811_223606.dump` (990K, 104 tabelas validadas
  com `pg_restore -l` **dentro do container** — no host o `pg_restore` dá falso negativo de "0 TABLE DATA").
- Imagens anteriores marcadas como `codewithcj/sparkyfitness{,_server}:rollback-20260811` antes do rebuild.
- Dados preservados (idênticos antes/depois): `foods`=1367, `food_entries`=615, `exercise_entries`=143,
  `sleep_entries`=26, users=2.
- Testes: **2.945 passando**, 1 falhando — a mesma `outboundProxy.test.ts` ambiental de sempre (undici/Node 26).
- A VM `odysseus` estava **parada** no início; subiu com `colima start odysseus` e o stack voltou junto.
- `pnpm` não está mais instalado no host — os testes rodaram com
  `SparkyFitnessServer/node_modules/.bin/vitest run`. O build não depende disso (é dentro do container).
- ❗ **Não consegui fazer a leitura autenticada pela API** como nas vezes anteriores: o cookie do better-auth é
  assinado (prefixo `sparky.`) e o token cru do banco não basta. Verificação ficou em: migration aplicada,
  contagens intactas, `/api/health` UP, guard de auth devolvendo 401, frontend servindo bundle novo e a suíte de testes.
  **Vale abrir o app e conferir o diário na tela.**

### 2026-08-07 — App atualizado para **v1.6.1** (build local); trabalho local de treino substituído pelo upstream
- Git `personalizacao` `844c0212` → `08546e65` (rebase sobre upstream, os 2 commits de docs recolocados por cima + este registro),
  `main` `1d4f4df5` → `22415819`. **44 commits** do upstream, tag **v1.6.1**. Push com `--force-with-lease`.
- **Nenhuma migration nova** — os 202 arquivos de `db/migrations/` são idênticos dos dois lados. O banco **não foi recriado**;
  só servidor e frontend. RLS reaplicada no boot.
- **App rebuildado LOCALMENTE** (backend 1,16 GB, frontend 105 MB). O primeiro build falhou por erro transitório de rede
  no `pnpm install` dentro do container; repetir o comando resolveu.
- Backup pré-update: `~/.sparkyfitness/backups/sparky_pre_upstream_20260807_230044.dump` (968K, 104 tabelas validadas).
- Dados preservados: `food_entries`=605, `foods`=1367, `meal_plan_template_assignments`=133, users=2, `water_intake`=17.
  Diário de 07/08 conferido pela API: 19 itens, como esperado do template.
- ⚠️ **Trabalho local não commitado foi substituído pelo upstream** (5 conflitos, todos resolvidos a favor do upstream):
  - Classificação de atividade: o `classifyHealthActivity` local (correspondência exata) foi superado pelo
    `resolveActivityMapping` do upstream (radicais, qualificadores de esteira/ergômetro, modalidade explícita do cliente).
    Duas divergências deliberadas do upstream: musculação vira `weight_reps` (não `duration`) e **não existe** categoria
    `Flexibility` — ioga/pilates caem em `Cardio`.
  - `avg_heart_rate`: o upstream **deriva no servidor** a partir de `hr_samples` (`workoutTelemetryDerivation.ts`).
    A linha local ficava *antes* do spread `...telemetry`, então seria sobrescrita — e como o mobile passou a enviar
    `hr_samples` em vez de `avgHeartRate`, ela gravaria `null`.
  - Nada foi apagado: patch em `~/.sparkyfitness/backups/local_uncommitted_20260807_200529.patch` (343 linhas),
    os 3 arquivos fora do git em `~/.sparkyfitness/backups/superseded_healthActivityCategory_20260807_200529/`,
    e a entrada `stash@{0}` no repo.
  - Os 3 arquivos saíram do repo porque `healthDataHandlers.workout.test.ts` afirmava o comportamento antigo
    e deixaria a suíte vermelha para sempre.
- Ajustes locais de infra (`127.0.0.1:5432` nos dois compose de dev) sobreviveram e convivem com a mudança do upstream
  no mesmo arquivo (`GARMIN_MICROSERVICE_URL` parametrizado).
- **Teste falhando que NÃO é regressão:** `tests/outboundProxy.test.ts` (1 de 3.107) quebra com `ENOTFOUND proxied.test`
  só na variante de `fetch` nativo — as de axios passam. É o undici não herdando o proxy neste Node 26, ambiente e não código.
- **Este runbook (§1) foi corrigido:** dizia "não é build local" e "puxa imagens novas", contradizendo §2/§3.

### 2026-08-01 — App atualizado para **v1.6.0** (build local); 2º usuário + compartilhamento família
- Git `personalizacao` `906aaa57` → `5552a21c` (rebase sobre upstream), `main` `36661741` → `d9eca4f5`. **217 commits** do upstream, tag **v1.6.0**. Push com `--force-with-lease`.
- **App rebuildado LOCALMENTE** (server `83a23f49`, front `ce7064df`); imagens antigas salvas como `:rollback-20260801`. Backup pré-update: `~/.sparkyfitness/backups/sparky_backup_preupdate_20260801_204528.dump` (~801K).
- **5 migrations novas** aplicadas no boot (spray medication, múltiplos meal plans ativos, distância/modalidade de treino, formato de hora, workout preset set distance). RLS reaplicada, health UP.
- Dados preservados: users=2, foods=721, meals=942, food_entries=59, family_access=2.
- **2º usuário (família):** `agatha.criar@gmail.com` (role `user`), criado via `POST /api/auth/sign-up/email`. **Compartilhamento família BIDIRECIONAL só-leitura** (2 linhas em `family_access`, perms `can_view_food_library`+`can_view_exercise_library`+`can_view_reports`, todas `can_manage_*`=false). `can_view_reports` inclui leitura de diário/medidas/relatórios/**medicações**.
- **Este runbook (§2 e §3) foi corrigido:** git agora é **rebase** (não ff-only) e app é **build local** (não `docker compose pull`).

### 2026-07-10 — Git avançado para `78b31c26`; app mantido em v0.17.3
- Git `personalizacao`/`main` `04b94639` → `78b31c26` (13 commits, ff) e enviados ao fork.
- Sem migrations novas; docker-compose intocado. Novidades no fonte: import CSV de saúde (medidas/sono/vitais/atividade/hidratação), auto-transcode HEIC→JPEG na IA, marcação de dias com foto no calendário, francês no YAZIO.
- **App NÃO atualizado:** imagens `:latest` ainda de 06/jul (v0.17.3, já em uso). Nada a puxar.

### 2026-07-09 — Git avançado para `04b94639`; app mantido em v0.17.3
- Git `personalizacao` e `main` atualizados `2a7e0d8f` → `04b94639` (ff, 82 commits) e enviados ao fork.
- **App NÃO atualizado:** as imagens `:latest` ainda são de 06/jul (v0.17.3 = digest `6aa7d983…`, já em uso).
  Os 82 commits (inclui migrations `add_passkey_registration_tickets` e `add_workout_session_columns`,
  workouts v2, import de comida com overwrite, validação de URL de IA) **ainda não foram publicados como imagem**.
- Backup pré-check: `backups/SparkyFitness_20260709_204219_preupdate` (dump 748K + sql.gz 316K, 94 tabelas).
- **Ação pendente:** quando o Docker Hub publicar tag > v0.17.3, rodar o runbook do §3 (as 2 migrations aplicam no boot).

### 2026-07-08 — Atualização para v1.5.0 / server 0.17.3
- Git `personalizacao` atualizado `22b3b780` → `2a7e0d8f` (ff, sem conflitos); `main` espelhado; ambos no fork.
- App atualizado: `pull` das imagens `:latest` (republicadas em 06/jul) + `up -d`.
- **Backup pré-update:** `backups/SparkyFitness_20260708_130419_preupdate` (dump 616K + sql.gz 308K, 68 tabelas).
- **Migrations aplicadas no boot** (todas OK): `add_custom_nutrient_aliases`, `add_onboarding_skipped`,
  `add_child_meal_to_meal_foods` (meal-to-meal), `add_cycle_tracking_schema` (10 tabelas de ciclo/gravidez),
  `fix_googlehealth_sleep_date_anchor`. RLS reaplicado.
- **Dados preservados:** foods=721, meals=942, meal_foods=2932, providers=5, users=1.
- **Novidades habilitadas:** Cycle Hub (período/gravidez/TTC), mood tags melhorados, tradução `pt`,
  frontend non-root (8080), remoção do SparkyFitnessMCP (virou rota `/mcp` in-process), fix de sleep do Google Health.
