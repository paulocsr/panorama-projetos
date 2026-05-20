# Panorama EVM

Dashboard de acompanhamento de projetos baseado na metodologia **Earned Value Management (EVM)** do PMI. Roda 100% no browser, sem instalação, sem servidor e sem dependências de build.

---

## Como funciona

A ferramenta é composta por dois arquivos:

| Arquivo | Função |
|---|---|
| `panorama-evm.html` | A página — abre direto no browser ou pode ser hospedada |
| `projetos-evm.xlsx` | A planilha — onde você mantém os dados dos seus projetos |

O fluxo de uso é simples: você preenche a planilha no Excel ou Google Planilhas, faz o upload na página, e todos os indicadores são calculados e exibidos automaticamente.

---

## Funcionalidades

**Aba Panorama EVM**
- Cartões de KPI consolidado: BAC total, AC acumulado, EAC projetado e contagem RAG
- Tabela de projetos com CPI, SPI, % executado, BAC, VAC e próximo marco
- Gráfico de dispersão CPI × SPI (posiciona cada projeto no quadrante de saúde)
- Gráfico de riscos abertos por severidade (Alto / Médio / Baixo)
- Classificação RAG automática (🟢 Verde / 🟡 Amarelo / 🔴 Vermelho) com base em CPI, SPI e riscos abertos
- Tooltips explicativos em todos os indicadores (passe o mouse sobre RAG, CPI, SPI, % Exec, BAC, VAC)
- Glossário EVM completo com fórmulas (seção expansível)

**Aba WBS**
- Visualização em árvore top-down (org chart): nível 0 no topo, fases lado a lado, entregáveis abaixo
- Cores por nível de hierarquia
- Botões para expandir e recolher ramos

**Geral**
- Campos não preenchidos na planilha ficam editáveis diretamente na interface
- Exportação de volta para `.xlsx` com as edições feitas na página
- Nenhum dado fica armazenado na página — o código é público, os dados ficam com você

---

## Como usar

### 1. Baixe os arquivos
Clone o repositório ou baixe `panorama-evm.html` e `projetos-evm.xlsx`.

### 2. Preencha a planilha
Abra `projetos-evm.xlsx` no Excel ou Google Planilhas. A planilha tem quatro abas:

- **PROJETOS** — uma linha por projeto com os campos base do EVM (`BAC`, `% Planejado`, `% Executado`, `AC`). Os demais campos são opcionais.
- **MARCOS** — marcos e entregas com datas e status.
- **RISCOS** — registro de riscos com probabilidade (1–5) e impacto (1–5). Score e severidade são calculados automaticamente pela página.
- **WBS** — estrutura analítica do trabalho com código, nível e descrição de cada item.

Campos marcados com `*` são usados nos cálculos. Os demais podem ficar em branco e ser preenchidos direto na página depois.

### 3. Abra a página e carregue a planilha
Abra `panorama-evm.html` no browser (duplo clique no arquivo). Clique em **Carregar .xlsx** e selecione sua planilha preenchida.

### 4. Acompanhe e edite
Navegue entre as abas **Panorama EVM** e **WBS**. Campos em branco aparecem com destaque e podem ser editados com um clique.

### 5. Exporte
Clique em **Exportar .xlsx** para salvar um novo arquivo com todas as edições feitas na página.

---

## Indicadores calculados automaticamente

A partir de `BAC`, `% Planejado`, `% Executado` e `AC`, a página calcula:

| Indicador | Fórmula | O que significa |
|---|---|---|
| PV | BAC × % Planejado | Valor que deveria estar gasto até hoje |
| EV | BAC × % Executado | Valor do trabalho realmente entregue |
| CV | EV − AC | Variação de custo (positivo = abaixo do orçamento) |
| SV | EV − PV | Variação de prazo (positivo = adiantado) |
| CPI | EV / AC | Eficiência de custo |
| SPI | EV / PV | Eficiência de cronograma |
| EAC | BAC / CPI | Custo total projetado |
| ETC | EAC − AC | Quanto ainda falta gastar |
| VAC | BAC − EAC | Estouro ou economia esperada no final |

**Regra RAG:**
- 🟢 Verde: CPI ≥ 0,95 **e** SPI ≥ 0,95 **e** sem risco alto aberto
- 🟡 Amarelo: algum índice entre 0,85–0,95, ou risco alto aberto
- 🔴 Vermelho: CPI < 0,85 **ou** SPI < 0,85, ou estouro confirmado

---

## Hospedagem no GitHub Pages

Para acessar a página de qualquer computador:

1. Faça o fork ou clone deste repositório
2. Vá em **Settings → Pages**
3. Em *Source*, selecione `main` e pasta `/root`
4. Aguarde alguns instantes — sua página estará disponível em `https://seuusuario.github.io/nome-do-repo`

O código da página fica público, mas **os dados nunca saem do seu computador** — a planilha é carregada localmente pelo browser e não é enviada a nenhum servidor.

---

## Tecnologias

- [SheetJS](https://sheetjs.com/) — leitura e escrita de arquivos `.xlsx`
- [Chart.js](https://www.chartjs.org/) — gráficos de dispersão e barras
- HTML + CSS + JavaScript puro — sem framework, sem build, sem dependências locais
