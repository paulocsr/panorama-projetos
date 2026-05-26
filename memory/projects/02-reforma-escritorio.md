# REF-TER — Reforma do andar térreo

> ⚠️ **Projeto de exemplo** — gerado automaticamente para demonstrar o sistema. Substitua pelos dados reais.

## 1. Identificação
- **Codinome:** REF-TER
- **Nome completo:** Reforma do andar térreo — sede SP
- **Sponsor:** Carlos Menezes (Facilities Manager)
- **Gerente de projeto:** Paulo
- **Descrição:** Reforma de 1.200 m² no andar térreo da sede SP: novo layout aberto, 8 salas de reunião, copa ampliada e troca de piso/iluminação.

## 2. Linha de base
- **Início:** 2026-02-01
- **Fim previsto:** 2026-08-15
- **Duração:** 6,5 meses
- **BAC:** R$ 320.000
- **Escopo principal:**
  - Demolição parcial e descarte
  - Drywall (12 paredes, 8 salas)
  - Elétrica + lógica (rede CAT6A)
  - Piso vinílico industrial
  - Pintura + mobiliário (separado, fora do escopo deste projeto)

## 3. Status atual — corte 2026-05-18
| Métrica | Valor | Observação |
|---------|-------|------------|
| % planejado | 50% | conforme cronograma |
| % executado | 42% | atrasado em 8pp |
| **PV** | R$ 160.000 | |
| **EV** | R$ 134.400 | |
| **AC** | R$ 148.000 | |
| **CV** | −R$ 13.600 | estourando |
| **SV** | −R$ 25.600 | atrasado |
| **CPI** | 0,91 | eficiência abaixo |
| **SPI** | 0,84 | atraso significativo |
| **EAC** | R$ 351.648 | estouro projetado R$ 31.648 |
| **VAC** | −R$ 31.648 | |
| **RAG** | 🟡 **Amarelo** | |

## 4. Marcos
| ID | Marco | Previsto | Realizado | Status |
|----|-------|----------|-----------|--------|
| M1 | Demolição concluída | 2026-02-28 | 2026-03-05 | ✅ (5d atraso) |
| M2 | Drywall + elétrica grossa | 2026-04-30 | 2026-05-10 | ✅ (10d atraso) |
| M3 | Entrega completa do drywall | 2026-06-05 | — | 🔜 próximo |
| M4 | Piso e pintura | 2026-07-15 | — | |
| M5 | Entrega final | 2026-08-15 | — | risco de slip |

## 5. RAID

### Riscos
| ID | Risco | P | I | Score | Sev | Resposta | Resp | Data |
|----|-------|---|---|-------|-----|----------|------|------|
| R1 | Fornecedor de drywall atrasou entrega de chapas | 5 | 3 | 15 | **Alto** | Aprovado fornecedor secundário emergencial; +R$ 8k | Carlos | 2026-04-22 |
| R2 | Chuvas atrasam serviços externos (calhas) | 3 | 2 | 6 | Médio | Reprogramar para janelas secas | Paulo | 2026-03-10 |
| R3 | Possível necessidade de reforço estrutural não-previsto | 2 | 5 | 10 | Médio | Inspeção estrutural agendada para 28/mai | Paulo | 2026-05-12 |

### Issues
- **I1** — Drywall do fornecedor primário atrasou 12 dias na entrega (R1 materializado parcialmente).

### Dependências
- Liberação da prefeitura para descarte de entulho classe A — recebida 2026-02-20.

## 6. Decisões
- **2026-02-01** — Empreiteira escolhida: ConstruirJá Ltda. Decisor: Carlos.
- **2026-04-22** — Aprovado fornecedor secundário de drywall (Steel Frame BR). Decisor: Carlos. Impacto: +R$ 8.000 no orçamento, −5 dias no atraso projetado.
- **2026-05-12** — Solicitada inspeção estrutural antes de avançar para piso. Decisor: Paulo. Justificativa: trinca pequena em viga durante demolição.

## 7. Próximos passos
- [ ] Receber inspeção estrutural — 28/mai — engenheiro contratado
- [ ] Confirmar entrega completa do drywall — 05/jun — Carlos
- [ ] Replanejar cronograma se inspeção indicar reforço — 30/mai — Paulo

## 8. Histórico de status
| Data | RAG | CPI | SPI | Nota |
|------|-----|-----|-----|------|
| 2026-05-18 | 🟡 | 0,91 | 0,84 | Atraso acumulado + trinca em viga |
| 2026-04-30 | 🟡 | 0,94 | 0,89 | Drywall atrasou, fornecedor secundário aprovado |
| 2026-03-31 | 🟢 | 0,98 | 0,95 | Demolição concluída com leve atraso |
| 2026-02-28 | 🟢 | 1,00 | 0,98 | Início ligeiramente atrasado pela papelada |
