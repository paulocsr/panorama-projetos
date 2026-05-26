# Metodologia — como acompanho projetos

> Esta é a metodologia padrão usada neste sistema. EVM (Earned Value Management) baseado em PMI/PMBOK.

## Princípios

1. **Tudo medido em R$**. Mesmo cronograma — quando converto progresso em EV, vira valor monetário. Isso permite comparar projetos de tamanhos diferentes.
2. **Baseline congelada**. PV não muda depois da linha de base aprovada. Se o escopo muda, é mudança formal (change request) com nova baseline.
3. **% de execução é objetivo**. Uso entregáveis concretos (marcos atingidos, pacotes de trabalho completos) — não "feeling" do time.
4. **RAG semanal, EVM mensal**. Status verde/amarelo/vermelho atualizo toda semana. Recalculo PV/EV/AC e índices uma vez por mês (ou quando há evento relevante).

## Cadência

| Quando | O que faço |
|--------|-----------|
| **Diário** (sob demanda) | Briefing dos itens em `TASKS.md` + bloqueios abertos |
| **Semanal** | Status report com RAG, marcos da semana, riscos novos, ações |
| **Mensal** | Recalculo EVM (PV/EV/AC, CPI, SPI, EAC) e revisão do RAID |
| **Por evento** | Mudança de escopo, materialização de risco, mudança de sponsor |

## Estrutura de cada projeto

Todo arquivo em `memory/projects/` segue o mesmo esqueleto:

```
1. Identificação        — codinome, nome, sponsor, gerente, descrição
2. Linha de base        — datas, BAC, escopo principal, marcos
3. Status atual         — data de corte, %PV, %EV, AC, CV, SV, CPI, SPI, EAC, VAC, RAG
4. Marcos               — tabela com previsto / atual / status
5. RAID                 — Risks, Assumptions, Issues, Dependencies
6. Decisões             — log datado de decisões importantes
7. Próximos passos      — ações com responsável e data
8. Histórico de status  — snapshot semanal/mensal
```

## Como classificar RAG

Regra-base (pode flexibilizar caso a caso, mas documente):

- **Verde** 🟢: `CPI ≥ 0,95` E `SPI ≥ 0,95` E sem risco aberto severidade alta.
- **Amarelo** 🟡: um dos índices entre 0,85 e 0,95, OU risco alto aberto sem plano de resposta.
- **Vermelho** 🔴: qualquer índice < 0,85, OU estouro confirmado de prazo/orçamento, OU sponsor escalou.

## Como capturar mudanças

Toda mudança que afete escopo, prazo ou orçamento vira:
1. Uma entrada no log de decisões do projeto (com data, decisor, justificativa).
2. Uma tarefa em `TASKS.md` (se houver ação derivada).
3. Atualização da linha de base — se aprovada formalmente, anote `Baseline v2` com a data.
