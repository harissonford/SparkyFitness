# Relatório de Seed — Refeições e Alimentos (SparkyFitness)

_Gerado a partir dos dados reais do banco. Usuário: harisson.ford8@gmail.com_

Total de refeições neste seed: **100**

## Modelo de dados (como ler as quantidades)

- Cada alimento tem uma **variante base por 100 g**. A quantidade de cada ingrediente na refeição está em **gramas (g)**.
- A nutrição de cada item = valor por 100 g × (gramas / 100). O **total da refeição** é a soma dos itens.
- **Fonte** de cada alimento: `taco` = valores aproximados da Tabela TACO; `openfoodfacts` = dados reais do Open Food Facts Brasil.

## ⚠️ Observação sobre itens "aproximados" (ex.: Misto quente)

Alguns itens da leva TACO são **alimentos compostos aproximados**, e NÃO foram decompostos em ingredientes. Exemplos e o que representam:

- **Misto quente (aprox.)** — 1 item único, ~280 kcal/100 g. A refeição "Lanche: Misto quente" usa **150 g** desse item (≈ um misto quente médio). **Não** foi modelado como "2 fatias de pão + 1 fatia de mussarela + 1 fatia de presunto".
- **Feijoada, Coxinha de frango frita, Pastel de carne frito, Strogonoff de frango** — idem: valores agregados por 100 g, não decompostos.

Se você quiser, dá para **reconstruir esses pratos como receitas compostas de verdade** (ex.: misto quente = 2 fatias de pão de forma 50 g + 1 fatia de mussarela 20 g + 1 fatia de presunto 15 g + manteiga 5 g). É só pedir.

### Referência de porções caseiras (aproximado)

| Item | 1 unidade/fatia ≈ |
|---|---|
| Pão francês | 50 g (1 unidade) |
| Fatia de pão de forma | 25 g |
| Fatia de queijo/presunto | 15–20 g |
| Ovo | 50 g (1 unidade) |
| Banana | 80–100 g (1 unidade) |
| Concha de arroz | 100–120 g |
| Concha de feijão | 80–100 g |
| Filé de frango | 100–120 g |

---

## Café da manhã (12)

### Café da manhã: Aveia + Banana

**Total:** ~378 kcal · 13.3 g proteína · 62 g carbo · 10.1 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Aveia em flocos | 40 g | 158 | 5.6 | 26.6 | 3.4 | taco |
| Banana prata | 100 g | 98 | 1.3 | 26 | 0.1 | taco |
| Leite integral | 200 g | 122 | 6.4 | 9.4 | 6.6 | taco |

### Café da manhã: Cuscuz + Ovo frito

**Total:** ~280 kcal · 12 g proteína · 31.1 g carbo · 11.9 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Cuscuz de milho cozido | 120 g | 136 | 2.6 | 30.4 | 0.7 | taco |
| Ovo frito | 60 g | 144 | 9.4 | 0.7 | 11.2 | taco |

### Café da manhã: Iogurte + Aveia + Banana

**Total:** ~279 kcal · 12.3 g proteína · 42.2 g carbo · 7.7 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Aveia em flocos | 30 g | 118 | 4.2 | 20 | 2.5 | taco |
| Banana nanica | 80 g | 74 | 1.1 | 19 | 0.1 | taco |
| Iogurte natural integral | 170 g | 87 | 7 | 3.2 | 5.1 | taco |

### Café da manhã: Mamão + Aveia

**Total:** ~186 kcal · 5.4 g proteína · 37.4 g carbo · 2.7 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Aveia em flocos | 30 g | 118 | 4.2 | 20 | 2.5 | taco |
| Mamão formosa | 150 g | 68 | 1.2 | 17.4 | 0.1 | taco |

### Café da manhã: Ovos mexidos + Pão integral

**Total:** ~362 kcal · 20.7 g proteína · 26.8 g carbo · 19.6 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Ovo mexido | 120 g | 235 | 16 | 1.8 | 17.9 | taco |
| Pão integral | 50 g | 127 | 4.7 | 24.9 | 1.8 | taco |

### Café da manhã: Pão de forma + Manteiga + Queijo

**Total:** ~298 kcal · 11.5 g proteína · 25.4 g carbo · 17.3 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Manteiga com sal | 10 g | 73 | 0 | 0 | 8.2 | taco |
| Pão de forma tradicional | 50 g | 127 | 4.7 | 24.4 | 1.5 | taco |
| Queijo mussarela | 30 g | 99 | 6.8 | 0.9 | 7.6 | taco |

### Café da manhã: Pão de queijo

**Total:** ~290 kcal · 3.7 g proteína · 32.4 g carbo · 15.8 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Pão de queijo assado | 80 g | 290 | 3.7 | 32.4 | 15.8 | taco |

### Café da manhã: Pão francês + Ovo mexido + Queijo

**Total:** ~386 kcal · 19.9 g proteína · 31.5 g carbo · 19.5 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Ovo mexido | 80 g | 157 | 10.6 | 1.2 | 11.9 | taco |
| Pão francês | 50 g | 150 | 4 | 29.3 | 1.6 | taco |
| Queijo minas frescal | 30 g | 79 | 5.2 | 1 | 6.1 | taco |

### Café da manhã: Pão integral + Requeijão

**Total:** ~178 kcal · 6.6 g proteína · 25.6 g carbo · 6.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Pão integral | 50 g | 127 | 4.7 | 24.9 | 1.8 | taco |
| Requeijão cremoso | 20 g | 51 | 1.9 | 0.7 | 4.5 | taco |

### Café da manhã: Tapioca + Queijo

**Total:** ~298 kcal · 7 g proteína · 48.5 g carbo · 8.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Queijo minas frescal | 40 g | 106 | 7 | 1.3 | 8.1 | taco |
| Tapioca (goma hidratada) | 80 g | 192 | 0 | 47.2 | 0.1 | taco |

### Café da manhã: Tapioca com ovo

**Total:** ~349 kcal · 10.6 g proteína · 48.4 g carbo · 12 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Ovo mexido | 80 g | 157 | 10.6 | 1.2 | 11.9 | taco |
| Tapioca (goma hidratada) | 80 g | 192 | 0 | 47.2 | 0.1 | taco |

### Café da manhã: Vitamina de banana com aveia

**Total:** ~369 kcal · 13.5 g proteína · 57.7 g carbo · 10.9 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Aveia em flocos | 30 g | 118 | 4.2 | 20 | 2.5 | taco |
| Banana prata | 100 g | 98 | 1.3 | 26 | 0.1 | taco |
| Leite integral | 250 g | 153 | 8 | 11.8 | 8.3 | taco |

---

## Lanche (10)

### Lanche: Banana + Amendoim

**Total:** ~234 kcal · 8.1 g proteína · 31.1 g carbo · 11.1 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Amendoim torrado | 25 g | 136 | 6.8 | 5.1 | 11 | taco |
| Banana prata | 100 g | 98 | 1.3 | 26 | 0.1 | taco |

### Lanche: Frutas (mamão e banana)

**Total:** ~132 kcal · 2 g proteína · 34.7 g carbo · 0.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Banana prata | 80 g | 78 | 1 | 20.8 | 0.1 | taco |
| Mamão formosa | 120 g | 54 | 1 | 13.9 | 0.1 | taco |

### Lanche: Iogurte + Banana

**Total:** ~160 kcal · 8.1 g proteína · 22.3 g carbo · 5.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Banana nanica | 80 g | 74 | 1.1 | 19 | 0.1 | taco |
| Iogurte natural integral | 170 g | 87 | 7 | 3.2 | 5.1 | taco |

### Lanche: Iogurte com aveia

**Total:** ~205 kcal · 11.1 g proteína · 23.2 g carbo · 7.6 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Aveia em flocos | 30 g | 118 | 4.2 | 20 | 2.5 | taco |
| Iogurte natural integral | 170 g | 87 | 7 | 3.2 | 5.1 | taco |

### Lanche: Maçã + Amendoim

**Total:** ~209 kcal · 7.2 g proteína · 24.8 g carbo · 11 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Amendoim torrado | 25 g | 136 | 6.8 | 5.1 | 11 | taco |
| Maçã Fuji com casca | 130 g | 73 | 0.4 | 19.8 | 0 | taco |

### Lanche: Misto quente

**Total:** ~420 kcal · 19.5 g proteína · 42 g carbo · 19.5 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Misto quente (aprox.) | 150 g | 420 | 19.5 | 42 | 19.5 | taco |

### Lanche: Pão de queijo (lanche)

**Total:** ~218 kcal · 2.8 g proteína · 24.3 g carbo · 11.9 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Pão de queijo assado | 60 g | 218 | 2.8 | 24.3 | 11.9 | taco |

### Lanche: Pão francês + Requeijão

**Total:** ~201 kcal · 5.9 g proteína · 30 g carbo · 6 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Pão francês | 50 g | 150 | 4 | 29.3 | 1.6 | taco |
| Requeijão cremoso | 20 g | 51 | 1.9 | 0.7 | 4.5 | taco |

### Lanche: Pão integral com queijo

**Total:** ~226 kcal · 11.5 g proteína · 25.8 g carbo · 9.3 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Pão integral | 50 g | 127 | 4.7 | 24.9 | 1.8 | taco |
| Queijo mussarela | 30 g | 99 | 6.8 | 0.9 | 7.6 | taco |

### Lanche: Tapioca com queijo

**Total:** ~274 kcal · 7 g proteína · 42.6 g carbo · 8.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Queijo minas frescal | 40 g | 106 | 7 | 1.3 | 8.1 | taco |
| Tapioca (goma hidratada) | 70 g | 168 | 0 | 41.3 | 0.1 | taco |

---

## Almoço (24)

### Almoço: Arroz + carioca + Carne moída refogada

**Total:** ~533 kcal · 41.5 g proteína · 57.7 g carbo · 14.6 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Carne moída (acém) refogada | 120 g | 254 | 32 | 0 | 13.7 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz + carioca + Contrafilé bovino grelhado

**Total:** ~612 kcal · 47.9 g proteína · 57.7 g carbo · 20.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Contrafilé bovino grelhado | 120 g | 334 | 38.4 | 0 | 19.2 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz + carioca + Filé de tilápia grelhado

**Total:** ~432 kcal · 41 g proteína · 57.7 g carbo · 3.7 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Filé de tilápia grelhado | 120 g | 154 | 31.4 | 0 | 2.8 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz + carioca + Frango grelhado

**Total:** ~469 kcal · 47.9 g proteína · 57.7 g carbo · 4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Frango grelhado (peito, sem pele) | 120 g | 191 | 38.4 | 0 | 3 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz + carioca + Linguiça de porco grelhada

**Total:** ~634 kcal · 35.9 g proteína · 57.7 g carbo · 28.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Linguiça de porco grelhada | 120 g | 355 | 26.4 | 0 | 27.2 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz + carioca + Ovo frito

**Total:** ~566 kcal · 28.2 g proteína · 59.1 g carbo · 23.3 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Ovo frito | 120 g | 288 | 18.7 | 1.4 | 22.3 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz + preto + Carne moída refogada

**Total:** ~534 kcal · 41.3 g proteína · 58.1 g carbo · 14.6 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Carne moída (acém) refogada | 120 g | 254 | 32 | 0 | 13.7 | taco |
| Feijão preto cozido | 100 g | 77 | 4.5 | 14 | 0.5 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz + preto + Contrafilé bovino grelhado

**Total:** ~613 kcal · 47.6 g proteína · 58.1 g carbo · 20.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Contrafilé bovino grelhado | 120 g | 334 | 38.4 | 0 | 19.2 | taco |
| Feijão preto cozido | 100 g | 77 | 4.5 | 14 | 0.5 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz + preto + Filé de tilápia grelhado

**Total:** ~433 kcal · 40.6 g proteína · 58.1 g carbo · 3.7 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Feijão preto cozido | 100 g | 77 | 4.5 | 14 | 0.5 | taco |
| Filé de tilápia grelhado | 120 g | 154 | 31.4 | 0 | 2.8 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz + preto + Frango grelhado

**Total:** ~470 kcal · 47.6 g proteína · 58.1 g carbo · 4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Feijão preto cozido | 100 g | 77 | 4.5 | 14 | 0.5 | taco |
| Frango grelhado (peito, sem pele) | 120 g | 191 | 38.4 | 0 | 3 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz + preto + Linguiça de porco grelhada

**Total:** ~635 kcal · 35.6 g proteína · 58.1 g carbo · 28.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Feijão preto cozido | 100 g | 77 | 4.5 | 14 | 0.5 | taco |
| Linguiça de porco grelhada | 120 g | 355 | 26.4 | 0 | 27.2 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz + preto + Ovo frito

**Total:** ~567 kcal · 27.9 g proteína · 59.5 g carbo · 23.3 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Feijão preto cozido | 100 g | 77 | 4.5 | 14 | 0.5 | taco |
| Ovo frito | 120 g | 288 | 18.7 | 1.4 | 22.3 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz integral + carioca + Carne moída refogada

**Total:** ~527 kcal · 41.7 g proteína · 54.2 g carbo · 15.8 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Carne moída (acém) refogada | 120 g | 254 | 32 | 0 | 13.7 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz integral + carioca + Contrafilé bovino grelhado

**Total:** ~606 kcal · 48.1 g proteína · 54.2 g carbo · 21.4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Contrafilé bovino grelhado | 120 g | 334 | 38.4 | 0 | 19.2 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz integral + carioca + Filé de tilápia grelhado

**Total:** ~426 kcal · 41.1 g proteína · 54.2 g carbo · 4.9 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Filé de tilápia grelhado | 120 g | 154 | 31.4 | 0 | 2.8 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz integral + carioca + Frango grelhado

**Total:** ~463 kcal · 48.1 g proteína · 54.2 g carbo · 5.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Frango grelhado (peito, sem pele) | 120 g | 191 | 38.4 | 0 | 3 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz integral + carioca + Linguiça de porco grelhada

**Total:** ~628 kcal · 36.1 g proteína · 54.2 g carbo · 29.4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Linguiça de porco grelhada | 120 g | 355 | 26.4 | 0 | 27.2 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz integral + carioca + Ovo frito

**Total:** ~560 kcal · 28.4 g proteína · 55.7 g carbo · 24.5 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Ovo frito | 120 g | 288 | 18.7 | 1.4 | 22.3 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz integral + preto + Carne moída refogada

**Total:** ~528 kcal · 41.4 g proteína · 54.6 g carbo · 15.8 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Carne moída (acém) refogada | 120 g | 254 | 32 | 0 | 13.7 | taco |
| Feijão preto cozido | 100 g | 77 | 4.5 | 14 | 0.5 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz integral + preto + Contrafilé bovino grelhado

**Total:** ~607 kcal · 47.8 g proteína · 54.6 g carbo · 21.4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Contrafilé bovino grelhado | 120 g | 334 | 38.4 | 0 | 19.2 | taco |
| Feijão preto cozido | 100 g | 77 | 4.5 | 14 | 0.5 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz integral + preto + Filé de tilápia grelhado

**Total:** ~427 kcal · 40.8 g proteína · 54.6 g carbo · 4.9 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Feijão preto cozido | 100 g | 77 | 4.5 | 14 | 0.5 | taco |
| Filé de tilápia grelhado | 120 g | 154 | 31.4 | 0 | 2.8 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz integral + preto + Frango grelhado

**Total:** ~464 kcal · 47.8 g proteína · 54.6 g carbo · 5.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Feijão preto cozido | 100 g | 77 | 4.5 | 14 | 0.5 | taco |
| Frango grelhado (peito, sem pele) | 120 g | 191 | 38.4 | 0 | 3 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz integral + preto + Linguiça de porco grelhada

**Total:** ~629 kcal · 35.8 g proteína · 54.6 g carbo · 29.4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Feijão preto cozido | 100 g | 77 | 4.5 | 14 | 0.5 | taco |
| Linguiça de porco grelhada | 120 g | 355 | 26.4 | 0 | 27.2 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

### Almoço: Arroz integral + preto + Ovo frito

**Total:** ~561 kcal · 28.1 g proteína · 56.1 g carbo · 24.5 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Alface crespa | 40 g | 4 | 0.5 | 0.7 | 0.1 | taco |
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Feijão preto cozido | 100 g | 77 | 4.5 | 14 | 0.5 | taco |
| Ovo frito | 120 g | 288 | 18.7 | 1.4 | 22.3 | taco |
| Tomate | 40 g | 6 | 0.4 | 1.2 | 0.1 | taco |

---

## Almoço reforçado (24)

### Almoço reforçado: Arroz + Feijão + Carne moída refogada + Batata frita

**Total:** ~683 kcal · 42.9 g proteína · 77.1 g carbo · 22.3 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Batata frita | 60 g | 160 | 2.3 | 21.4 | 7.8 | taco |
| Carne moída (acém) refogada | 120 g | 254 | 32 | 0 | 13.7 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |

### Almoço reforçado: Arroz + Feijão + Carne moída refogada + Couve refogada

**Total:** ~576 kcal · 41.6 g proteína · 61 g carbo · 17.5 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Carne moída (acém) refogada | 120 g | 254 | 32 | 0 | 13.7 | taco |
| Couve refogada | 60 g | 54 | 1 | 5.2 | 3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |

### Almoço reforçado: Arroz + Feijão + Carne moída refogada + Farofa

**Total:** ~739 kcal · 41.5 g proteína · 108.5 g carbo · 14.7 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Carne moída (acém) refogada | 120 g | 254 | 32 | 0 | 13.7 | taco |
| Farinha de mandioca torrada | 60 g | 217 | 1 | 52.7 | 0.2 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |

### Almoço reforçado: Arroz + Feijão + Carne moída refogada + Purê de batata

**Total:** ~580 kcal · 41.7 g proteína · 64.2 g carbo · 16.6 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Carne moída (acém) refogada | 120 g | 254 | 32 | 0 | 13.7 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Purê de batata | 60 g | 58 | 1.1 | 8.4 | 2.2 | taco |

### Almoço reforçado: Arroz + Feijão + Contrafilé bovino grelhado + Batata frita

**Total:** ~762 kcal · 49.2 g proteína · 77.1 g carbo · 27.8 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Batata frita | 60 g | 160 | 2.3 | 21.4 | 7.8 | taco |
| Contrafilé bovino grelhado | 120 g | 334 | 38.4 | 0 | 19.2 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |

### Almoço reforçado: Arroz + Feijão + Contrafilé bovino grelhado + Couve refogada

**Total:** ~656 kcal · 48 g proteína · 61 g carbo · 23 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Contrafilé bovino grelhado | 120 g | 334 | 38.4 | 0 | 19.2 | taco |
| Couve refogada | 60 g | 54 | 1 | 5.2 | 3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |

### Almoço reforçado: Arroz + Feijão + Contrafilé bovino grelhado + Farofa

**Total:** ~818 kcal · 47.9 g proteína · 108.5 g carbo · 20.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Contrafilé bovino grelhado | 120 g | 334 | 38.4 | 0 | 19.2 | taco |
| Farinha de mandioca torrada | 60 g | 217 | 1 | 52.7 | 0.2 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |

### Almoço reforçado: Arroz + Feijão + Contrafilé bovino grelhado + Purê de batata

**Total:** ~659 kcal · 48 g proteína · 64.2 g carbo · 22.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Contrafilé bovino grelhado | 120 g | 334 | 38.4 | 0 | 19.2 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Purê de batata | 60 g | 58 | 1.1 | 8.4 | 2.2 | taco |

### Almoço reforçado: Arroz + Feijão + Filé de tilápia grelhado + Batata frita

**Total:** ~582 kcal · 42.3 g proteína · 77.1 g carbo · 11.4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Batata frita | 60 g | 160 | 2.3 | 21.4 | 7.8 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Filé de tilápia grelhado | 120 g | 154 | 31.4 | 0 | 2.8 | taco |

### Almoço reforçado: Arroz + Feijão + Filé de tilápia grelhado + Couve refogada

**Total:** ~476 kcal · 41 g proteína · 61 g carbo · 6.6 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Couve refogada | 60 g | 54 | 1 | 5.2 | 3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Filé de tilápia grelhado | 120 g | 154 | 31.4 | 0 | 2.8 | taco |

### Almoço reforçado: Arroz + Feijão + Filé de tilápia grelhado + Farofa

**Total:** ~638 kcal · 41 g proteína · 108.5 g carbo · 3.7 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Farinha de mandioca torrada | 60 g | 217 | 1 | 52.7 | 0.2 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Filé de tilápia grelhado | 120 g | 154 | 31.4 | 0 | 2.8 | taco |

### Almoço reforçado: Arroz + Feijão + Filé de tilápia grelhado + Purê de batata

**Total:** ~479 kcal · 41.1 g proteína · 64.2 g carbo · 5.7 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Filé de tilápia grelhado | 120 g | 154 | 31.4 | 0 | 2.8 | taco |
| Purê de batata | 60 g | 58 | 1.1 | 8.4 | 2.2 | taco |

### Almoço reforçado: Arroz + Feijão + Frango grelhado + Batata frita

**Total:** ~619 kcal · 49.2 g proteína · 77.1 g carbo · 11.6 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Batata frita | 60 g | 160 | 2.3 | 21.4 | 7.8 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Frango grelhado (peito, sem pele) | 120 g | 191 | 38.4 | 0 | 3 | taco |

### Almoço reforçado: Arroz + Feijão + Frango grelhado + Couve refogada

**Total:** ~513 kcal · 48 g proteína · 61 g carbo · 6.8 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Couve refogada | 60 g | 54 | 1 | 5.2 | 3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Frango grelhado (peito, sem pele) | 120 g | 191 | 38.4 | 0 | 3 | taco |

### Almoço reforçado: Arroz + Feijão + Frango grelhado + Farofa

**Total:** ~675 kcal · 47.9 g proteína · 108.5 g carbo · 4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Farinha de mandioca torrada | 60 g | 217 | 1 | 52.7 | 0.2 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Frango grelhado (peito, sem pele) | 120 g | 191 | 38.4 | 0 | 3 | taco |

### Almoço reforçado: Arroz + Feijão + Frango grelhado + Purê de batata

**Total:** ~516 kcal · 48 g proteína · 64.2 g carbo · 6 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Frango grelhado (peito, sem pele) | 120 g | 191 | 38.4 | 0 | 3 | taco |
| Purê de batata | 60 g | 58 | 1.1 | 8.4 | 2.2 | taco |

### Almoço reforçado: Arroz + Feijão + Linguiça de porco grelhada + Batata frita

**Total:** ~783 kcal · 37.2 g proteína · 77.1 g carbo · 35.8 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Batata frita | 60 g | 160 | 2.3 | 21.4 | 7.8 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Linguiça de porco grelhada | 120 g | 355 | 26.4 | 0 | 27.2 | taco |

### Almoço reforçado: Arroz + Feijão + Linguiça de porco grelhada + Couve refogada

**Total:** ~677 kcal · 36 g proteína · 61 g carbo · 31 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Couve refogada | 60 g | 54 | 1 | 5.2 | 3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Linguiça de porco grelhada | 120 g | 355 | 26.4 | 0 | 27.2 | taco |

### Almoço reforçado: Arroz + Feijão + Linguiça de porco grelhada + Farofa

**Total:** ~840 kcal · 35.9 g proteína · 108.5 g carbo · 28.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Farinha de mandioca torrada | 60 g | 217 | 1 | 52.7 | 0.2 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Linguiça de porco grelhada | 120 g | 355 | 26.4 | 0 | 27.2 | taco |

### Almoço reforçado: Arroz + Feijão + Linguiça de porco grelhada + Purê de batata

**Total:** ~681 kcal · 36 g proteína · 64.2 g carbo · 30.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Linguiça de porco grelhada | 120 g | 355 | 26.4 | 0 | 27.2 | taco |
| Purê de batata | 60 g | 58 | 1.1 | 8.4 | 2.2 | taco |

### Almoço reforçado: Arroz + Feijão + Ovo frito + Batata frita

**Total:** ~716 kcal · 29.5 g proteína · 78.5 g carbo · 30.9 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Batata frita | 60 g | 160 | 2.3 | 21.4 | 7.8 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Ovo frito | 120 g | 288 | 18.7 | 1.4 | 22.3 | taco |

### Almoço reforçado: Arroz + Feijão + Ovo frito + Couve refogada

**Total:** ~610 kcal · 28.3 g proteína · 62.4 g carbo · 26.1 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Couve refogada | 60 g | 54 | 1 | 5.2 | 3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Ovo frito | 120 g | 288 | 18.7 | 1.4 | 22.3 | taco |

### Almoço reforçado: Arroz + Feijão + Ovo frito + Farofa

**Total:** ~773 kcal · 28.2 g proteína · 109.9 g carbo · 23.3 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Farinha de mandioca torrada | 60 g | 217 | 1 | 52.7 | 0.2 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Ovo frito | 120 g | 288 | 18.7 | 1.4 | 22.3 | taco |

### Almoço reforçado: Arroz + Feijão + Ovo frito + Purê de batata

**Total:** ~614 kcal · 28.4 g proteína · 65.6 g carbo · 25.3 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Feijão carioca cozido | 100 g | 76 | 4.8 | 13.6 | 0.5 | taco |
| Ovo frito | 120 g | 288 | 18.7 | 1.4 | 22.3 | taco |
| Purê de batata | 60 g | 58 | 1.1 | 8.4 | 2.2 | taco |

---

## Jantar (24)

### Jantar: Carne moída refogada + Arroz integral cozido

**Total:** ~429 kcal · 36.2 g proteína · 36.7 g carbo · 15 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz integral cozido | 120 g | 149 | 3.1 | 31 | 1.2 | taco |
| Beterraba cozida | 80 g | 26 | 1 | 5.8 | 0.1 | taco |
| Carne moída (acém) refogada | 120 g | 254 | 32 | 0 | 13.7 | taco |

### Jantar: Carne moída refogada + Macarrão cozido

**Total:** ~460 kcal · 37.5 g proteína · 34.6 g carbo · 19.2 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Carne moída (acém) refogada | 120 g | 254 | 32 | 0 | 13.7 | taco |
| Couve refogada | 80 g | 72 | 1.4 | 7 | 4 | taco |
| Macarrão cozido | 120 g | 133 | 4.1 | 27.6 | 1.6 | taco |

### Jantar: Carne moída refogada + Mandioca cozida

**Total:** ~444 kcal · 34.9 g proteína · 39.3 g carbo · 16.4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Carne moída (acém) refogada | 120 g | 254 | 32 | 0 | 13.7 | taco |
| Espinafre refogado | 80 g | 40 | 2.2 | 3.2 | 2.3 | taco |
| Mandioca cozida | 120 g | 150 | 0.7 | 36.1 | 0.4 | taco |

### Jantar: Carne moída refogada + Purê de batata

**Total:** ~390 kcal · 35.9 g proteína · 20.3 g carbo · 18.4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Brócolis cozido | 80 g | 20 | 1.7 | 3.5 | 0.4 | taco |
| Carne moída (acém) refogada | 120 g | 254 | 32 | 0 | 13.7 | taco |
| Purê de batata | 120 g | 115 | 2.2 | 16.8 | 4.3 | taco |

### Jantar: Contrafilé bovino grelhado + Arroz integral cozido

**Total:** ~508 kcal · 42.6 g proteína · 36.7 g carbo · 20.5 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz integral cozido | 120 g | 149 | 3.1 | 31 | 1.2 | taco |
| Beterraba cozida | 80 g | 26 | 1 | 5.8 | 0.1 | taco |
| Contrafilé bovino grelhado | 120 g | 334 | 38.4 | 0 | 19.2 | taco |

### Jantar: Contrafilé bovino grelhado + Macarrão cozido

**Total:** ~539 kcal · 43.8 g proteína · 34.6 g carbo · 24.8 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Contrafilé bovino grelhado | 120 g | 334 | 38.4 | 0 | 19.2 | taco |
| Couve refogada | 80 g | 72 | 1.4 | 7 | 4 | taco |
| Macarrão cozido | 120 g | 133 | 4.1 | 27.6 | 1.6 | taco |

### Jantar: Contrafilé bovino grelhado + Mandioca cozida

**Total:** ~524 kcal · 41.3 g proteína · 39.3 g carbo · 21.9 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Contrafilé bovino grelhado | 120 g | 334 | 38.4 | 0 | 19.2 | taco |
| Espinafre refogado | 80 g | 40 | 2.2 | 3.2 | 2.3 | taco |
| Mandioca cozida | 120 g | 150 | 0.7 | 36.1 | 0.4 | taco |

### Jantar: Contrafilé bovino grelhado + Purê de batata

**Total:** ~469 kcal · 42.2 g proteína · 20.3 g carbo · 23.9 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Brócolis cozido | 80 g | 20 | 1.7 | 3.5 | 0.4 | taco |
| Contrafilé bovino grelhado | 120 g | 334 | 38.4 | 0 | 19.2 | taco |
| Purê de batata | 120 g | 115 | 2.2 | 16.8 | 4.3 | taco |

### Jantar: Filé de tilápia grelhado + Arroz integral cozido

**Total:** ~328 kcal · 35.6 g proteína · 36.7 g carbo · 4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz integral cozido | 120 g | 149 | 3.1 | 31 | 1.2 | taco |
| Beterraba cozida | 80 g | 26 | 1 | 5.8 | 0.1 | taco |
| Filé de tilápia grelhado | 120 g | 154 | 31.4 | 0 | 2.8 | taco |

### Jantar: Filé de tilápia grelhado + Macarrão cozido

**Total:** ~359 kcal · 36.9 g proteína · 34.6 g carbo · 8.3 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Couve refogada | 80 g | 72 | 1.4 | 7 | 4 | taco |
| Filé de tilápia grelhado | 120 g | 154 | 31.4 | 0 | 2.8 | taco |
| Macarrão cozido | 120 g | 133 | 4.1 | 27.6 | 1.6 | taco |

### Jantar: Filé de tilápia grelhado + Mandioca cozida

**Total:** ~344 kcal · 34.3 g proteína · 39.3 g carbo · 5.4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Espinafre refogado | 80 g | 40 | 2.2 | 3.2 | 2.3 | taco |
| Filé de tilápia grelhado | 120 g | 154 | 31.4 | 0 | 2.8 | taco |
| Mandioca cozida | 120 g | 150 | 0.7 | 36.1 | 0.4 | taco |

### Jantar: Filé de tilápia grelhado + Purê de batata

**Total:** ~289 kcal · 35.3 g proteína · 20.3 g carbo · 7.5 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Brócolis cozido | 80 g | 20 | 1.7 | 3.5 | 0.4 | taco |
| Filé de tilápia grelhado | 120 g | 154 | 31.4 | 0 | 2.8 | taco |
| Purê de batata | 120 g | 115 | 2.2 | 16.8 | 4.3 | taco |

### Jantar: Frango grelhado + Arroz integral cozido

**Total:** ~365 kcal · 42.6 g proteína · 36.7 g carbo · 4.3 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz integral cozido | 120 g | 149 | 3.1 | 31 | 1.2 | taco |
| Beterraba cozida | 80 g | 26 | 1 | 5.8 | 0.1 | taco |
| Frango grelhado (peito, sem pele) | 120 g | 191 | 38.4 | 0 | 3 | taco |

### Jantar: Frango grelhado + Macarrão cozido

**Total:** ~396 kcal · 43.8 g proteína · 34.6 g carbo · 8.6 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Couve refogada | 80 g | 72 | 1.4 | 7 | 4 | taco |
| Frango grelhado (peito, sem pele) | 120 g | 191 | 38.4 | 0 | 3 | taco |
| Macarrão cozido | 120 g | 133 | 4.1 | 27.6 | 1.6 | taco |

### Jantar: Frango grelhado + Mandioca cozida

**Total:** ~381 kcal · 41.3 g proteína · 39.3 g carbo · 5.7 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Espinafre refogado | 80 g | 40 | 2.2 | 3.2 | 2.3 | taco |
| Frango grelhado (peito, sem pele) | 120 g | 191 | 38.4 | 0 | 3 | taco |
| Mandioca cozida | 120 g | 150 | 0.7 | 36.1 | 0.4 | taco |

### Jantar: Frango grelhado + Purê de batata

**Total:** ~326 kcal · 42.2 g proteína · 20.3 g carbo · 7.7 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Brócolis cozido | 80 g | 20 | 1.7 | 3.5 | 0.4 | taco |
| Frango grelhado (peito, sem pele) | 120 g | 191 | 38.4 | 0 | 3 | taco |
| Purê de batata | 120 g | 115 | 2.2 | 16.8 | 4.3 | taco |

### Jantar: Linguiça de porco grelhada + Arroz integral cozido

**Total:** ~530 kcal · 30.6 g proteína · 36.7 g carbo · 28.5 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz integral cozido | 120 g | 149 | 3.1 | 31 | 1.2 | taco |
| Beterraba cozida | 80 g | 26 | 1 | 5.8 | 0.1 | taco |
| Linguiça de porco grelhada | 120 g | 355 | 26.4 | 0 | 27.2 | taco |

### Jantar: Linguiça de porco grelhada + Macarrão cozido

**Total:** ~560 kcal · 31.8 g proteína · 34.6 g carbo · 32.8 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Couve refogada | 80 g | 72 | 1.4 | 7 | 4 | taco |
| Linguiça de porco grelhada | 120 g | 355 | 26.4 | 0 | 27.2 | taco |
| Macarrão cozido | 120 g | 133 | 4.1 | 27.6 | 1.6 | taco |

### Jantar: Linguiça de porco grelhada + Mandioca cozida

**Total:** ~545 kcal · 29.3 g proteína · 39.3 g carbo · 29.9 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Espinafre refogado | 80 g | 40 | 2.2 | 3.2 | 2.3 | taco |
| Linguiça de porco grelhada | 120 g | 355 | 26.4 | 0 | 27.2 | taco |
| Mandioca cozida | 120 g | 150 | 0.7 | 36.1 | 0.4 | taco |

### Jantar: Linguiça de porco grelhada + Purê de batata

**Total:** ~490 kcal · 30.2 g proteína · 20.3 g carbo · 32 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Brócolis cozido | 80 g | 20 | 1.7 | 3.5 | 0.4 | taco |
| Linguiça de porco grelhada | 120 g | 355 | 26.4 | 0 | 27.2 | taco |
| Purê de batata | 120 g | 115 | 2.2 | 16.8 | 4.3 | taco |

### Jantar: Ovo frito + Arroz integral cozido

**Total:** ~462 kcal · 22.9 g proteína · 38.2 g carbo · 23.6 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz integral cozido | 120 g | 149 | 3.1 | 31 | 1.2 | taco |
| Beterraba cozida | 80 g | 26 | 1 | 5.8 | 0.1 | taco |
| Ovo frito | 120 g | 288 | 18.7 | 1.4 | 22.3 | taco |

### Jantar: Ovo frito + Macarrão cozido

**Total:** ~493 kcal · 24.2 g proteína · 36 g carbo · 27.9 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Couve refogada | 80 g | 72 | 1.4 | 7 | 4 | taco |
| Macarrão cozido | 120 g | 133 | 4.1 | 27.6 | 1.6 | taco |
| Ovo frito | 120 g | 288 | 18.7 | 1.4 | 22.3 | taco |

### Jantar: Ovo frito + Mandioca cozida

**Total:** ~478 kcal · 21.6 g proteína · 40.8 g carbo · 25 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Espinafre refogado | 80 g | 40 | 2.2 | 3.2 | 2.3 | taco |
| Mandioca cozida | 120 g | 150 | 0.7 | 36.1 | 0.4 | taco |
| Ovo frito | 120 g | 288 | 18.7 | 1.4 | 22.3 | taco |

### Jantar: Ovo frito + Purê de batata

**Total:** ~423 kcal · 22.6 g proteína · 21.8 g carbo · 27 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Brócolis cozido | 80 g | 20 | 1.7 | 3.5 | 0.4 | taco |
| Ovo frito | 120 g | 288 | 18.7 | 1.4 | 22.3 | taco |
| Purê de batata | 120 g | 115 | 2.2 | 16.8 | 4.3 | taco |

---

## Coxinha + Suco (1)

### Coxinha + Suco

**Total:** ~318 kcal · 10.2 g proteína · 30 g carbo · 16.8 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Coxinha de frango frita | 120 g | 318 | 10.2 | 30 | 16.8 | taco |

---

## Feijoada (prato) (1)

### Feijoada (prato)

**Total:** ~410 kcal · 30.4 g proteína · 40.6 g carbo · 22.8 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Feijoada | 350 g | 410 | 30.4 | 40.6 | 22.8 | - |

---

## Macarrão + Carne moída + Queijo ralado (1)

### Macarrão + Carne moída + Queijo ralado

**Total:** ~465 kcal · 36.3 g proteína · 42 g carbo · 17.8 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Carne moída (acém) refogada | 100 g | 212 | 26.7 | 0 | 11.4 | taco |
| Macarrão cozido | 180 g | 200 | 6.1 | 41.4 | 2.3 | taco |
| Queijo minas frescal | 20 g | 53 | 3.5 | 0.6 | 4 | taco |

---

## Pastel de carne (2 un) (1)

### Pastel de carne (2 un)

**Total:** ~473 kcal · 12 g proteína · 42 g carbo · 27 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Pastel de carne frito | 150 g | 473 | 12 | 42 | 27 | taco |

---

## Strogonoff de frango + Arroz + Batata frita (1)

### Strogonoff de frango + Arroz + Batata frita

**Total:** ~626 kcal · 27.6 g proteína · 74.3 g carbo · 23.4 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz branco cozido | 150 g | 192 | 3.8 | 42.1 | 0.3 | taco |
| Batata frita | 60 g | 160 | 2.3 | 21.4 | 7.8 | taco |
| Strogonoff de frango | 180 g | 274 | 21.6 | 10.8 | 15.3 | taco |

---

## Tilápia + Arroz integral + Brócolis (1)

### Tilápia + Arroz integral + Brócolis

**Total:** ~403 kcal · 45.3 g proteína · 43.1 g carbo · 5.5 g gordura

| Ingrediente | Quantidade | kcal | Prot (g) | Carbo (g) | Gord (g) | Fonte |
|---|---|---|---|---|---|---|
| Arroz integral cozido | 150 g | 186 | 3.9 | 38.7 | 1.5 | taco |
| Brócolis cozido | 100 g | 25 | 2.1 | 4.4 | 0.5 | taco |
| Filé de tilápia grelhado | 150 g | 192 | 39.3 | 0 | 3.5 | taco |

---

