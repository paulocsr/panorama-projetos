# Memória de trabalho

## Eu
**Paulo** — Gerente de Projetos. Acompanha múltiplos projetos em paralelo usando metodologia **EVM (Earned Value Management)** do PMI. Não usa ferramenta dedicada no PC pessoal; no trabalho usa MS Project. Esta pasta é o sistema central de acompanhamento.

## Como Paulo trabalha
- Mede saúde de projeto por **EVM**: PV, EV, AC, CV, CPI, SPI (ver `memory/glossary.md`).
- Classifica projetos por **RAG** (verde / amarelo / vermelho) com base em CPI e SPI combinados.
- Quer rotinas de: dashboard ao vivo, status report semanal, registro de riscos e decisões, briefing diário — sob demanda.

## Regra-RAG (heurística padrão)
- **Verde**: CPI ≥ 0,95 **e** SPI ≥ 0,95 **e** sem risco aberto de severidade alta.
- **Amarelo**: 0,85 ≤ CPI < 0,95 **ou** 0,85 ≤ SPI < 0,95 **ou** risco alto aberto.
- **Vermelho**: CPI < 0,85 **ou** SPI < 0,85 **ou** estouro confirmado de orçamento/prazo.

## Projetos ativos (exemplos)
| Codinome | Nome | Sponsor | RAG | Próximo marco |
|----------|------|---------|-----|---------------|
| **CRM-SF** | Implantação CRM Salesforce | Marta Borges (Diretora Comercial) | 🟢 Verde | UAT — 30/jun/2026 |
| **REF-TER** | Reforma do andar térreo | Carlos Menezes (Facilities) | 🟡 Amarelo | Entrega drywall — 05/jun/2026 |
| **ERP-CLOUD** | Migração ERP para Oracle Cloud | Ricardo Tavares (CFO) | 🔴 Vermelho | Go-live revisado — 31/ago/2026 |
| **LGPD-W2** | Programa LGPD — Wave 2 (RH + Marketing) | Lúcia Andrade (DPO) | 🟢 Verde | Mapa de dados RH — 12/jun/2026 |

Detalhes em `memory/projects/`.

## Pessoas-chave
| Apelido | Nome / Papel |
|---------|--------------|
| **Marta** | Marta Borges — Diretora Comercial (sponsor CRM-SF) |
| **Carlos** | Carlos Menezes — Facilities Manager (sponsor REF-TER) |
| **Ricardo** | Ricardo Tavares — CFO (sponsor ERP-CLOUD) |
| **Lúcia** | Lúcia Andrade — DPO (sponsor LGPD-W2) |

Detalhes em `memory/people/`.

## Termos / siglas
| Termo | Significado |
|-------|-------------|
| **EVM** | Earned Value Management |
| **PV** | Planned Value (Valor Planejado) |
| **EV** | Earned Value (Valor Agregado) |
| **AC** | Actual Cost (Custo Real) |
| **CV** | Cost Variance (EV − AC) |
| **SV** | Schedule Variance (EV − PV) |
| **CPI** | Cost Performance Index (EV / AC) |
| **SPI** | Schedule Performance Index (EV / PV) |
| **BAC** | Budget at Completion (orçamento total) |
| **EAC** | Estimate at Completion (estimativa de custo final) |
| **ETC** | Estimate to Complete (estimativa do que falta) |
| **VAC** | Variance at Completion (BAC − EAC) |
| **RAG** | Red / Amber / Green — semáforo de status |
| **RAID** | Risks, Assumptions, Issues, Dependencies |
| **UAT** | User Acceptance Testing |
| **DPO** | Data Protection Officer |

Glossário completo: `memory/glossary.md`.

## Preferências
- Idioma: português (Brasil).
- Datas: formato `dd/mmm/aaaa` em textos; `YYYY-MM-DD` em tabelas e arquivos.
- Moeda: BRL (R$).
- Relatórios curtos: bullets, sem prosa longa.
- Sempre que entregar status, indicar **CPI, SPI e RAG** logo no topo.
