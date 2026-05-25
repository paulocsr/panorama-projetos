# Plano — Sistema de Gestão de Projetos EVM v2

> Objetivo: ferramenta web para acompanhamento contínuo de projetos com metodologia EVM,
> começando como uso próprio e com arquitetura preparada para virar produto multi-usuário.

---

## 1. Decisões de arquitetura

### Stack recomendada (100% gratuita para começar)

| Camada | Ferramenta | Por quê |
|---|---|---|
| **Banco de dados + Auth** | [Supabase](https://supabase.com) | PostgreSQL real, Auth embutido, API REST automática, tempo real, free tier generoso (500 MB) |
| **Frontend** | HTML + JS puro (evolução do atual) | Você já conhece, sem framework novo para aprender |
| **Hospedagem** | [Vercel](https://vercel.com) | Deploy automático via GitHub, HTTPS grátis, custom domain depois |
| **PDF / relatório** | `html2pdf.js` (biblioteca JS) | Gera PDF no browser, sem servidor |
| **Charts** | Chart.js (já em uso) | Mantém o que funciona |

### Por que Supabase e não Firebase?
Supabase usa **SQL** — muito mais natural para dados relacionais de projetos (projetos → riscos → marcos → snapshots EVM). Firebase usa NoSQL, que complica consultas como "todos os riscos abertos de projetos com CPI < 0,85".

Além disso, o Supabase já tem **Row Level Security (RLS)** pronto — quando quiser virar produto multi-usuário, cada cliente enxerga só seus dados com alteração mínima no código.

---

## 2. O que aproveitar do sistema atual

| Componente | Status | Ação |
|---|---|---|
| Design system (CSS, cores, RAG pills, cards) | ✅ reaproveitado | Copiar diretamente |
| Cálculos EVM (calcEVM, fmtBRL, etc.) | ✅ reaproveitado | Copiar diretamente |
| Gráfico CPI × SPI (Chart.js) | ✅ reaproveitado | Copiar diretamente |
| WBS tree renderer | ✅ reaproveitado | Copiar diretamente |
| Tooltips flutuantes | ✅ reaproveitado | Copiar diretamente |
| Glossário EVM | ✅ reaproveitado | Copiar diretamente |
| Carga via planilha xlsx | ⚠️ descontinuado | Substituído por formulários + Supabase |

---

## 3. Banco de dados — estrutura das tabelas

```
users (gerenciado pelo Supabase Auth)
└── profiles: id, nome, email

projects
└── id, user_id, code, name, sponsor, description
    start_date, end_date_baseline, bac, rag (calculado), created_at

evm_snapshots          ← um registro por atualização de dados
└── id, project_id, snapshot_date
    pct_planned, pct_executed, ac, notes

milestones
└── id, project_id, code, description
    planned_date, actual_date, status, notes

raid_items             ← Riscos, Assumptions, Issues, Dependencies
└── id, project_id, type, description
    probability, impact, response, owner, status, date

wbs_items
└── id, project_id, wbs_code, level, description, parent_code

decisions
└── id, project_id, date, description, decision_maker, impact
```

---

## 4. Estrutura de páginas

```
login.html          → tela de login (Supabase Auth)
index.html          → dashboard: todos os projetos, KPIs consolidados, RAG
project.html        → detalhe do projeto: abas EVM | WBS | RAID | Marcos | Decisões
report.html         → status report gerado automaticamente, botão exportar PDF
```

### Navegação principal
```
[Dashboard] → clica em projeto → [Detalhe do Projeto]
                                         ├── Aba EVM (gráficos, snapshot atual + histórico)
                                         ├── Aba WBS (árvore)
                                         ├── Aba RAID (tabela de riscos/issues)
                                         ├── Aba Marcos (timeline)
                                         └── Aba Decisões (log)
                               → botão "Gerar Relatório" → [report.html]
```

---

## 5. Funcionalidades do MVP (fase 1)

### Obrigatório
- [x] Login com e-mail e senha (Supabase Auth)
- [x] CRUD de projetos (criar, editar, excluir)
- [x] Registro de snapshots EVM (atualizar % planejado, % executado, AC a qualquer momento)
- [x] Dashboard consolidado com CPI, SPI, RAG e gráfico CPI × SPI
- [x] RAID: adicionar/editar/fechar riscos e issues
- [x] Marcos: registrar datas previstas e realizadas
- [x] Status report automático com exportação em PDF
- [x] WBS visual

### Fora do MVP (fase 2)
- [ ] Multi-usuário por empresa (compartilhar projeto com outro PM)
- [ ] Histórico de EVM em gráfico de linha (evolução semana a semana)
- [ ] Notificações / alertas (projeto virou vermelho, marco vencendo)
- [ ] App mobile (PWA — Progressive Web App, sem precisar de loja de apps)
- [ ] Importação via planilha (reaproveitar o xlsx atual para onboarding)

---

## 6. Status report — o que gera automaticamente

Um clique em "Gerar Relatório" produz um documento com:

1. **Cabeçalho**: projeto, sponsor, data do corte, RAG atual
2. **EVM snapshot**: tabela PV / EV / AC / CV / SV / CPI / SPI / EAC / VAC
3. **Riscos abertos** (ordenados por severidade)
4. **Marcos**: próximos 3 e últimos concluídos
5. **Decisões recentes** (últimas 30 dias)
6. **Próximos passos** (RAID items com ação pendente)

Exporta como PDF via `html2pdf.js` — tudo no browser, sem servidor.

---

## 7. Plano de build — ordem das etapas

### Etapa 1 — Fundação (Supabase + login)
1. Criar conta no Supabase e configurar projeto
2. Criar tabelas conforme estrutura acima
3. Configurar autenticação (e-mail + senha)
4. Criar `login.html` com formulário de login

### Etapa 2 — Dashboard e projetos
5. Criar `index.html`: lista de projetos com cards RAG
6. Formulário para criar / editar projeto
7. Conexão ao Supabase via `@supabase/supabase-js` (CDN)

### Etapa 3 — Detalhe do projeto
8. Criar `project.html` com sistema de abas
9. Aba EVM: formulário de snapshot + exibição de CPI/SPI/RAG + Chart.js
10. Aba RAID: tabela + formulário de adição de risco/issue
11. Aba Marcos: lista + formulário
12. Aba WBS: carregar itens do banco + renderizar árvore (código atual)

### Etapa 4 — Status report
13. Criar `report.html`: layout de relatório estilizado
14. Integrar `html2pdf.js` para exportação em PDF

### Etapa 5 — Dados de exemplo e polish
15. Popular banco com os 4 projetos fictícios já existentes (CRM-SF, REF-TER, ERP-CLOUD, LGPD-W2)
16. Ajustes visuais e responsividade mobile

---

## 8. Caminho para produto (pós-MVP)

### Técnico (mudanças mínimas)
- Supabase RLS já está preparado para multi-usuário: adicionar `user_id` nas políticas
- Criar página de registro público (`register.html`)
- Adicionar planos (free / pro) via coluna `plan` na tabela `profiles`

### Comercial
| Modelo | Descrição |
|---|---|
| **SaaS freemium** | Gratuito até 2 projetos, pago para ilimitado |
| **Licença para empresa** | Uma instância por cliente (deploy próprio no Supabase deles) |
| **Serviço gerenciado** | Você configura e mantém para o cliente, cobrado mensalmente |

### Custos quando sair do free tier
- Supabase Pro: US$ 25/mês (banco ilimitado, backups, suporte)
- Vercel Pro: US$ 20/mês (só necessário com muito tráfego)
- Domínio próprio: ~R$ 50/ano

---

## 9. Perguntas abertas antes de começar a Etapa 1

1. **Nome do produto** — já tem ideia ou quer sugestões?
2. **Domínio futuro** — pretende comprar um domínio próprio ou hospedar em `seuusuario.vercel.app` por enquanto?
3. **Idioma da interface** — português somente, ou bilíngue (pt/en) desde o início pensando em vender fora?
4. **Logo / identidade visual** — manter o esquema de cores atual (azul escuro) ou partir do zero?
