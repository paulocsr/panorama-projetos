# ERP-CLOUD — Migração ERP para Oracle Cloud

> ⚠️ **Projeto de exemplo** — gerado automaticamente para demonstrar o sistema. Substitua pelos dados reais.

## 1. Identificação
- **Codinome:** ERP-CLOUD
- **Nome completo:** Migração SAP ECC 6.0 → Oracle Cloud ERP
- **Sponsor:** Ricardo Tavares (CFO)
- **Gerente de projeto:** Paulo
- **Descrição:** Substituir o SAP ECC on-premises por Oracle Cloud ERP. Inclui módulos Financeiro, Compras, Fiscal (Brasil) e integração com folha de pagamento (sistema externo TOTVS).

## 2. Linha de base
- **Início:** 2025-10-01
- **Fim previsto (baseline):** 2026-06-30
- **Duração baseline:** 9 meses
- **BAC:** R$ 2.400.000
- **Escopo principal:**
  - Implementação de 4 módulos
  - Migração de 8 anos de histórico contábil
  - Integração folha (TOTVS) bidirecional
  - Localizações fiscais BR (NFe, SPED, EFD)
  - Cutover e estabilização (3 meses)

## 3. Status atual — corte 2026-05-18
| Métrica | Valor | Observação |
|---------|-------|------------|
| % planejado | 88% | conforme cronograma original |
| % executado | 70% | atrasado em 18pp |
| **PV** | R$ 2.112.000 | |
| **EV** | R$ 1.680.000 | |
| **AC** | R$ 1.920.000 | |
| **CV** | −R$ 240.000 | estourando 10% do AC |
| **SV** | −R$ 432.000 | atraso material |
| **CPI** | 0,875 | abaixo do limiar |
| **SPI** | 0,795 | abaixo do limiar |
| **EAC** | R$ 2.742.857 | estouro projetado R$ 342.857 |
| **VAC** | −R$ 342.857 | |
| **RAG** | 🔴 **Vermelho** | |

> **Replanejamento em curso.** Go-live revisado para **2026-08-31** (proposta apresentada ao comitê). Aguardando aprovação.

## 4. Marcos
| ID | Marco | Previsto | Realizado | Status |
|----|-------|----------|-----------|--------|
| M1 | Kickoff e blueprint | 2025-10-01 | 2025-10-08 | ✅ |
| M2 | Configuração módulos FIN + Compras | 2026-01-31 | 2026-02-15 | ✅ |
| M3 | Integração folha — primeiro teste | 2026-03-15 | 2026-04-02 | ✅ |
| M4 | Localizações fiscais BR | 2026-04-30 | 2026-05-10 | ✅ |
| M5 | UAT integrado | 2026-05-15 | — | 🔴 atrasado |
| M6 | Go-live | 2026-06-30 | — | 🔴 inviável — revisar |

## 5. RAID

### Riscos
| ID | Risco | P | I | Score | Sev | Resposta | Resp | Data |
|----|-------|---|---|-------|-----|----------|------|------|
| R1 | Falha na integração com TOTVS folha | 4 | 5 | 20 | **Alto** | Força-tarefa com fornecedor; cenário B: integração via arquivo até estabilizar | Ricardo + Paulo | 2026-04-20 |
| R2 | Perda de 2 desenvolvedores-chave (saída) | 5 | 4 | 20 | **Alto** | Substitutos contratados; aceleração de knowledge transfer | Paulo | 2026-04-28 |
| R3 | Atraso impacta fechamento fiscal Q3 | 4 | 5 | 20 | **Alto** | Manter SAP ECC em paralelo até estabilização (custo +R$ 45k/mês) | Ricardo | 2026-05-05 |

### Issues
- **I1** — Integração com TOTVS falhou em UAT (R1 materializado). Status: em diagnóstico conjunto.
- **I2** — Dois devs deixaram o time entre 15 e 22/abril (R2 materializado). Status: substitutos onboarding.

### Dependências
- Comitê executivo precisa aprovar nova baseline até 2026-05-30.

## 6. Decisões
- **2025-10-01** — Adjudicação para Oracle + parceiro de implementação (DBA Cloud). Decisor: comitê CFO/CIO.
- **2026-03-20** — Adicionar módulo de Tesouraria ao escopo (CR-001). Decisor: Ricardo. Impacto: +R$ 180k no BAC (já incorporado).
- **2026-05-05** — Manter SAP ECC em paralelo após go-live por 60 dias. Decisor: Ricardo. Impacto: +R$ 90k.
- **2026-05-14** — Solicitação formal de replanejamento (nova baseline). Aguardando comitê de 2026-05-28.

## 7. Próximos passos
- [ ] Apresentar plano de replanejamento ao comitê — 28/mai — Paulo + Ricardo
- [ ] Concluir diagnóstico técnico da integração TOTVS — 25/mai — DBA Cloud
- [ ] Finalizar onboarding dos 2 devs substitutos — 31/mai — líder técnico

## 8. Histórico de status
| Data | RAG | CPI | SPI | Nota |
|------|-----|-----|-----|------|
| 2026-05-18 | 🔴 | 0,88 | 0,80 | UAT atrasado, replanejamento submetido |
| 2026-04-30 | 🔴 | 0,90 | 0,84 | Falha de integração + saída de 2 devs |
| 2026-03-31 | 🟡 | 0,96 | 0,92 | Integração folha começou a derrapar |
| 2026-02-28 | 🟢 | 1,00 | 0,98 | Dentro do plano |
