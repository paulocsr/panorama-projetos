# Glossário — EVM e gestão de projetos

## Indicadores de Earned Value Management (EVM)

### Métricas base

| Sigla | Nome | Como calcular | Significado |
|-------|------|---------------|-------------|
| **BAC** | Budget at Completion | Orçamento aprovado da linha de base | Quanto o projeto inteiro deveria custar |
| **PV** | Planned Value | `BAC × % planejado até a data` | Quanto eu deveria ter gastado até hoje, conforme cronograma |
| **EV** | Earned Value | `BAC × % realmente executado até a data` | O quanto de valor já foi entregue, em R$ |
| **AC** | Actual Cost | Soma dos gastos até a data | O quanto eu realmente gastei |

### Variações

| Sigla | Nome | Cálculo | Leitura |
|-------|------|---------|---------|
| **CV** | Cost Variance | `EV − AC` | Positivo = abaixo do orçamento. Negativo = estourando. |
| **SV** | Schedule Variance | `EV − PV` | Positivo = adiantado. Negativo = atrasado. |

### Índices de performance

| Sigla | Nome | Cálculo | Leitura |
|-------|------|---------|---------|
| **CPI** | Cost Performance Index | `EV / AC` | ≥ 1,0 eficiência boa. < 1,0 está gastando mais do que entrega. |
| **SPI** | Schedule Performance Index | `EV / PV` | ≥ 1,0 no prazo ou adiantado. < 1,0 atrasado. |

### Projeções para o fim

| Sigla | Nome | Cálculo padrão | Significado |
|-------|------|----------------|-------------|
| **EAC** | Estimate at Completion | `BAC / CPI` (cenário típico) | Quanto o projeto vai custar no total, mantida a performance atual |
| **ETC** | Estimate to Complete | `EAC − AC` | Quanto falta gastar |
| **VAC** | Variance at Completion | `BAC − EAC` | Quanto vou economizar (+) ou estourar (−) no final |

## Interpretação rápida (cheat sheet)

| CPI / SPI | Diagnóstico |
|-----------|-------------|
| CPI ≥ 1 e SPI ≥ 1 | Verde — projeto saudável |
| CPI < 1 e SPI ≥ 1 | Estourando custo, mas no prazo |
| CPI ≥ 1 e SPI < 1 | Atrasado, mas eficiente em custo |
| CPI < 1 e SPI < 1 | Atrasado e estourando — atenção máxima |

## Outras siglas comuns

| Sigla | Significado |
|-------|-------------|
| **RAG** | Red / Amber / Green — semáforo de status |
| **RAID** | Risks, Assumptions, Issues, Dependencies — log central |
| **WBS** | Work Breakdown Structure — EAP em PT |
| **EAP** | Estrutura Analítica do Projeto |
| **PMBOK** | Project Management Body of Knowledge (PMI) |
| **PMI** | Project Management Institute |
| **UAT** | User Acceptance Testing |
| **SOW** | Statement of Work |
| **TAP** | Termo de Abertura do Projeto |
| **PEP** | Plano de Execução do Projeto |
| **DPO** | Data Protection Officer |
| **LGPD** | Lei Geral de Proteção de Dados |
| **ERP** | Enterprise Resource Planning |
| **CRM** | Customer Relationship Management |

## Severidade de risco (escala usada nos projetos)

| Nível | Probabilidade × Impacto | Ação |
|-------|-------------------------|------|
| **Alto** | ≥ 12 (escala 1–5 × 1–5) | Plano de resposta obrigatório + escalonamento |
| **Médio** | 6–11 | Plano de resposta documentado |
| **Baixo** | ≤ 5 | Monitorar |
