# SparkyFitness — Documentação do Self-Host (personalização)

> Registro operacional da instância self-hosted (fork `harissonford/SparkyFitness`).
> Não faz parte do upstream — arquivo local do dono da instância.
> **Última atualização: 2026-07-08.**

---

## 1. Como este ambiente roda

- **Não é build local.** O app roda a partir das **imagens prontas** publicadas no Docker Hub:
  - `codewithcj/sparkyfitness:latest` (frontend)
  - `codewithcj/sparkyfitness_server:latest` (servidor)
  - `postgres:18.3-alpine` (banco)
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
- **Importante:** atualizar o *código-fonte* (git) **não** muda o app rodando. O app só muda quando você **puxa imagens novas** e recria os containers (ver §3).

---

## 2. Git — fork e branches

- `origin` = fork pessoal `github.com/harissonford/SparkyFitness`
- `upstream` = `github.com/CodeWithCJ/SparkyFitness`
- Branches:
  - `main` — espelha `upstream/main` (não editar; só fast-forward).
  - `personalizacao` — branch de trabalho. Hoje = `upstream/main` + ajustes locais (ver §5).

### Atualizar o git com o upstream (sem perder personalização)
```bash
git fetch upstream --prune

# guarda ajustes locais não commitados (bind 127.0.0.1)
git stash push -m "ajustes locais" docker/docker-compose.dev.yml docker/docker-compose.db_dev.yml

# atualiza a branch de trabalho
git checkout personalizacao
git merge --ff-only upstream/main      # ou 'git rebase upstream/main' se houver commits próprios

# reaplica os ajustes locais
git stash pop

# espelha main e envia ao fork
git branch -f main upstream/main
git push origin personalizacao main
```
> Se o `stash pop` conflitar: os ajustes locais são só a linha da porta do Postgres — resolver mantendo `"127.0.0.1:5432:5432"`.

---

## 3. Atualizar o APP (imagens + migrations) — runbook

> **Sempre faça backup antes (§4).** As migrations são aditivas, mas backup é obrigatório.

```bash
cd /Volumes/FORD_2TB/claudeAI/projetos/SparkyFitness
C="-p docker -f docker/docker-compose.prod.yml -f docker/docker-compose.local.yml"

# 1. Backup do banco (ver §4)

# 2. Puxa imagens novas
docker compose $C pull

# 3. Recria containers (o DB não é recriado; server aplica migrations no boot)
docker compose $C up -d

# 4. Acompanha as migrations
docker logs docker-sparkyfitness-server-1 2>&1 | grep -iE "migrat|RLS|listening"

# 5. Verifica saúde
docker ps --filter name=sparky --format 'table {{.Names}}\t{{.Status}}'
```

### Checar se há imagem nova publicada (antes de atualizar)
```bash
curl -s https://hub.docker.com/v2/repositories/codewithcj/sparkyfitness_server/tags/latest \
  | python3 -c "import sys,json;print(json.load(sys.stdin)['tag_last_pushed'])"
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
