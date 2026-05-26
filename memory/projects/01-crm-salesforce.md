# CRM-SF — Implantação CRM Salesforce

> ⚠️ **Projeto de exemplo** — gerado automaticamente para demonstrar o sistema. Substitua pelos dados reais.

## 1. Identificação
- **Codinome:** CRM-SF
- **Nome completo:** Implantação Salesforce Sales Cloud — substituição do CRM legado
- **Sponsor:** Marta Borges (Diretora Comercial)
- **Gerente de projeto:** Paulo
- **Descrição:** Substituir o CRM legado (Microsoft Dynamics 2015) por Salesforce Sales Cloud, com integração ao ERP e treinamento de 120 vendedores.

## 2. Linha de base
- **Início:** 2026-01-15
- **Fim previsto:** 2026-12-15
- **Duração:** 11 meses
- **BAC:** R$ 480.000
- **Escopo principal:**
  - Configuração da org Salesforce + objetos custom
  - Migração de dados do CRM legado (~85k contas, ~200k contatos)
  - Integração bidirecional com ERP (REST API)
  - Treinamento e go-live por região (4 ondas)
- **Marcos da baseline:** ver seção 4

## 3. Status atual — corte 2026-05-18
| Métrica | Valor | Observação |
|---------|-------|------------|
| % planejado | 38% | conforme cronograma |
| % executado | 40% | adiantado em 2pp |
| **PV** | R$ 182.400 | |
| **EV** | R$ 192.000 | |
| **AC** | R$ 185.000 | |
| **CV** | +R$ 7.000 | abaixo do orçamento |
| **SV** | +R$ 9.600 | adiantado |
| **CPI** | 1,04 | eficiência boa |
| **SPI** | 1,05 | dentro do ritmo |
| **EAC** | R$ 461.538 | provável economia de R$ 18.462 |
| **VAC** | +R$ 18.462 | |
| **RAG** | 🟢 **Verde** | |

## 4. Marcos
| ID | Marco | Previsto | Realizado | Status |
|----|-------|----------|-----------|--------|
| M1 | Kickoff e contrato com SI | 2026-01-15 | 2026-01-15 | ✅ |
| M2 | Configuração base aprovada | 2026-03-30 | 2026-03-28 | ✅ |
| M3 | Migração de contas concluída | 2026-05-15 | 2026-05-14 | ✅ |
| M4 | UAT da Onda 1 (SE/Sul) | 2026-06-30 | — | 🔜 próximo |
| M5 | Go-live Onda 1 | 2026-07-31 | — | |
| M6 | Go-live Onda 2 (NE/N) | 2026-09-30 | — | |
| M7 | Go-live final + encerramento | 2026-12-15 | — | |

## 5. RAID

### Riscos
| ID | Risco | P | I | Score | Sev | Resposta | Resp | Data |
|----|-------|---|---|-------|-----|----------|------|------|
| R1 | Adoção baixa pelos vendedores sênior | 3 | 4 | 12 | Alto | Plano de change management + champions por região | Marta | 2026-02-10 |
| R2 | Limites de API do ERP em horário comercial | 2 | 3 | 6 | Médio | Sincronização batch noturna + cache local | Paulo | 2026-04-02 |

### Issues
- Nenhuma aberta.

### Dependências
- ERP precisa expor endpoint `/accounts/v2` antes de 30/jun (dono: Ricardo / time ERP-CLOUD).

## 6. Decisões
- **2026-01-15** — Escolha do SI: Solvian Consulting (vencedor do RFP). Decisor: Marta. Justificativa: melhor proposta técnica e R$ 60k abaixo do segundo colocado.
- **2026-03-12** — Adicionar campo custom "Segmento Estratégico" no objeto Account. Decisor: Paulo + Marta. Impacto: +3 dias no cronograma, absorvido pelo buffer.

## 7. Próximos passos
- [ ] Preparar roteiro de UAT da Onda 1 — até 30/mai — Paulo
- [ ] Treinar 6 champions Sul + SE — primeira semana de junho — RH + Solvian
- [ ] Validar endpoint ERP `/accounts/v2` em sandbox — até 20/jun — Ricardo

## 8. Histórico de status
| Data | RAG | CPI | SPI | Nota |
|------|-----|-----|-----|------|
| 2026-05-18 | 🟢 | 1,04 | 1,05 | Migração de contas no prazo |
| 2026-04-30 | 🟢 | 1,02 | 1,01 | Config base entregue 2 dias antes |
| 2026-03-31 | 🟢 | 1,00 | 1,00 | Linha de base mantida |
