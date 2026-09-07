---
id: DATA-REPORT-CODE-001
folder_id: FS-IDX-005
tipo: relatorio
status: ativo
projeto: ECOSSISTEMA_15-08_FILESYSTEM
dominio: 01-master-index/04-reports
gerado_por: "Claude Code · workflow plugin-engineer-workflow-klbtix"
skills_aplicadas: [testing-strategy, code-review]
data: 2026-09-07
revisado_em: 2026-09-07
---

# Master Index · Repositórios de Código do Ecossistema Sas-Executar

Consolida a análise individual dos 6 repositórios GitHub do ecossistema, sob a governança das skills **testing-strategy** (estratégia e cobertura de testes) e **code-review** (qualidade, CI e higiene de revisão). Cada repositório recebeu, na branch `claude/plugin-engineer-workflow-klbtix`, um documento de análise individual referenciado na seção 4.

> **Nota de revisão:** a classificação de `Desyng-System-ecossitema.` foi corrigida após a publicação inicial. A primeira versão confiou no README do repositório ("não contém código de aplicação") sem inspecionar `apps/`/`packages/`. Investigando uma falha real de deploy no Vercel do PR daquele repositório, confirmou-se que ele contém um monorepo de implementação ativo (Astro + Next.js/Payload/Postgres). Ver seção 3 e o documento individual do repositório para o achado completo — inclusive o próprio README desatualizado, que hoje é um achado de code-review por si só.

## 1. Escopo e confirmação de acesso

| Repositório | Acesso confirmado | Branch padrão | Estado do repositório |
|---|---|---|---|
| `Sas-Executar/Sas-Executar` | ✅ leitura + escrita | `main` | Ativo, 30 branches (28 dependabot) |
| `Sas-Executar/CustoCognitivoBlog` | ✅ leitura + escrita | `main` | Ativo, 24 branches, alta velocidade de iteração |
| `Sas-Executar/Desyng-System-ecossitema.` | ✅ leitura + escrita | ⚠️ sem `main` (usa `claude/design-handoff-specs-ulc1r1`) | Ativo, monorepo de implementação real, build de produção quebrado no momento |
| `Sas-Executar/Maestr-Docs` | ✅ leitura + escrita | `main` | Ativo, vault de governança/taxonomia |
| `Sas-Executar/Cognitivo-Mapa` | ✅ leitura + escrita | `main` | Ativo, em produção (Vercel) |
| `Sas-Executar/programa-sas` | ✅ leitura + escrita | — | **Vazio, 0 commits, não inicializado** |

Usuário autenticado: `Sas-Executar` (App/PAT com escopo sobre os 6 repositórios listados). Nenhum repositório retornou erro de autorização — apenas `programa-sas` retornou `Git Repository is empty`, o que é estado de dados, não de permissão.

## 2. Metodologia

Cada repositório foi avaliado nos mesmos 5 eixos:
1. **Acesso e permissões** — confirmação de leitura/escrita e estado de branches.
2. **Papel no ecossistema** — o que o repositório entrega e para quem.
3. **Arquitetura** — stack, monorepo/tooling, padrões de fronteira.
4. **Testing strategy** — cobertura existente, gaps, recomendação priorizada (skill `testing-strategy`).
5. **Code review readiness** — lint/format/CI, higiene de branches, capacidade de revisão (skill `code-review`).

A partir disso, cada repositório foi posicionado em uma hierarquia única de maturidade de arquitetura/desenvolvimento. **Importante:** a documentação de um repositório (README) foi tratada como hipótese a verificar contra o conteúdo real do código, não como fonte de verdade — foi assim que a classificação original de `Desyng-System-ecossitema.` foi corrigida (seção 3).

## 3. Hierarquia de arquitetura e desenvolvimento — do mais ao menos desenvolvido

| # | Repositório | Categoria | Sinais de maturidade | Sinais de lacuna |
|---|---|---|---|---|
| 1 | **Sas-Executar/Sas-Executar** | Produto (SaaS canônico) | Turborepo+Bun, Biome, Playwright E2E com **gate de performance**, Vitest, IaC AWS (OIDC, sem credenciais estáticas), apps web+mobile (Expo/Tamagui), release semântico automatizado, `AGENTS.md` | Cobertura de teste não quantificada; `apps/mobile` sem gate de teste declarado; alto volume de PRs dependabot pendentes de triagem |
| 2 | **Sas-Executar/CustoCognitivoBlog** | Produto (CMS + Site) | pnpm monorepo, Next.js16+Payload3 e Astro, fronteira de tipos (`cms-types`), feature flag para rollout controlado (RC Scanner), CI configurado (`.github/workflows` presente), documentação de arquitetura e migração viva | Sem test runner/pasta de testes visível na raiz; migração Astro sem gate de paridade; branches de feature acumuladas sem limpeza; um projeto Vercel órfão (`payload-website-starter`) falhando |
| 3 | **Sas-Executar/Desyng-System-ecossitema.** | Produto (Blog + Admin) **+** especificação/handoff | Monorepo pnpm real: `apps/blog` (Astro), `apps/admin` (Next.js+Payload+Postgres, com `AGENTS.md`/`CLAUDE.md` próprios), `packages/{callout-protocol,design-tokens,ui}`; camada `design-system/` com governança de decisão formalizada (`SOT_RESOLUTION.md`, `OPEN_QUESTIONS.md`) | **Zero CI** (`.github/workflows` ausente); **build de produção do projeto Vercel `blog` quebrado agora** (módulo de workspace não resolvendo); sem branch `main`; README raiz desatualizado (declara "sem código de aplicação", o que é falso para `apps/`) |
| 4 | **Sas-Executar/Cognitivo-Mapa** | Produto (landing standalone) | Código de aplicação real **em produção**; contrato de dados versionado (`consultation-schema.json`); governança de claims editoriais | Sem build tooling, lint, teste ou CI; gaps de qualidade (Core Web Vitals, WCAG 2.2) autodeclarados no README — mas, ao menos, a documentação é honesta sobre o próprio estado |
| 5 | **Sas-Executar/Maestr-Docs** | Governança / conhecimento | Taxonomia de 14 domínios + registro central de Folder IDs (`CENTRAL_CONTROL.csv`), workflow de intake→classificação→canônico, submódulo git para skills Anthropic | Não é software executável — não se aplica CI/teste de código; depende de disciplina manual para manter o CSV sincronizado |
| 6 | **Sas-Executar/programa-sas** | Não inicializado | — | Repositório vazio: sem commits, sem branches, sem conteúdo a avaliar |

**Leitura da hierarquia:** os níveis 1–3 são produtos com código executável real; entre eles, o critério de desempate é a disciplina operacional (CI, saúde do deploy, documentação fiel ao código) — por isso `Desyng-System-ecossitema.` fica atrás de `CustoCognitivoBlog` apesar de escopo de implementação comparável. O nível 4 é software real porém sem nenhuma disciplina de engenharia (e, em compensação, com documentação honesta sobre isso). O nível 5 é infraestrutura de conhecimento (nenhum código para testar, por desenho). O nível 6 ainda não existe como projeto.

## 4. Análises individuais (link canônico)

| Repositório | Documento |
|---|---|
| Sas-Executar/Sas-Executar | `docs/governance/2026-09-07-repo-analysis-plugin-engineer.md` (branch `claude/plugin-engineer-workflow-klbtix`) |
| Sas-Executar/CustoCognitivoBlog | `docs/governance/2026-09-07-repo-analysis-plugin-engineer.md` (branch `claude/plugin-engineer-workflow-klbtix`) |
| Sas-Executar/Desyng-System-ecossitema. | `docs/governance/2026-09-07-repo-analysis-plugin-engineer.md` (branch `claude/plugin-engineer-workflow-klbtix` — **revisado**, ver nota no topo do documento) |
| Sas-Executar/Cognitivo-Mapa | `docs/2026-09-07-repo-analysis-plugin-engineer.md` (branch `claude/plugin-engineer-workflow-klbtix`) |
| Sas-Executar/Maestr-Docs | este documento |
| Sas-Executar/programa-sas | `docs/governance/2026-09-07-repo-analysis-plugin-engineer.md` (repositório inicializado nesta mesma rodada — ver seção 6) |

## 5. Relações entre repositórios

```
Desyng-System-ecossitema. (Blog/Astro + Admin/Payload, + spec/tokens em design-system/)
        │  fonte-da-verdade visual (design-system/) e possível implementação paralela/duplicada de Blog+Admin
        ▼
CustoCognitivoBlog (Site/Astro, CMS/Payload) ──┐
        │                                       │  integração futura
        ▼                                       ▼
Cognitivo-Mapa (landing standalone)  ──►  Scanner + VERA (ainda não conectados)
        │
        ▼
Sas-Executar/Sas-Executar (SaaS canônico: app web + mobile Expo)
        ▲
        │  governa/registra conhecimento e skills de todos os repositórios acima
Maestr-Docs (vault de governança, taxonomia, master index)

programa-sas — ainda sem papel definido no ecossistema (repositório vazio)
```

**Achado de governança:** `Desyng-System-ecossitema.` e `CustoCognitivoBlog` parecem implementar o mesmo domínio (Blog Astro + Admin/CMS Payload) em repositórios separados. Isso não foi confirmado como duplicação intencional (ex.: um é sandbox/handoff e o outro é produção) nem como divergência acidental — é uma pergunta em aberto que precisa de decisão humana antes de investir mais engenharia em qualquer um dos dois.

## 6. Recomendações de governança priorizadas

1. **Desyng-System-ecossitema. vs. CustoCognitivoBlog**: esclarecer com o responsável pelo produto se são o mesmo produto em migração, implementações paralelas intencionais, ou uma duplicação acidental — antes de investir mais engenharia em qualquer um dos dois.
2. **Desyng-System-ecossitema.**: corrigir o build quebrado do projeto Vercel `blog` (resolução do workspace `@executar/callout-protocol`), adicionar CI mínimo, promover `claude/design-handoff-specs-ulc1r1` a `main`, e atualizar o README raiz para não generalizar "sem código de aplicação".
3. **programa-sas**: definir o propósito do repositório antes de qualquer código ser adicionado.
4. **Sas-Executar/Sas-Executar**: triagem semanal das branches `dependabot/*` e definição de gate de teste para `apps/mobile`.
5. **CustoCognitivoBlog**: gate de paridade E2E para a migração Astro, limpeza de branches de feature já mescladas, e remoção/correção do projeto Vercel órfão `payload-website-starter`.
6. **Cognitivo-Mapa**: CI mínimo (lint + validação de schema) e teste automatizado de Core Web Vitals/acessibilidade, dado que os próprios gaps já estão documentados no README.
7. **Maestr-Docs**: manter esta seção de `04-reports` como o índice mestre vivo — cada nova análise de repositório deve ser adicionada aqui, não substituída. **Tratar o README de um repositório como hipótese a verificar contra o código, nunca como fonte de verdade**, conforme demonstrado pela correção nesta própria rodada.

## 7. Próximos passos

- [x] Abrir PR (draft) em cada um dos 6 repositórios a partir da branch `claude/plugin-engineer-workflow-klbtix` (`programa-sas` sem PR possível — ver documento individual).
- [ ] Levar a pergunta da seção 5 (Desyng vs. CustoCognitivoBlog) ao responsável pelo produto.
- [ ] Revisar e, quando aprovado, promover as recomendações da seção 6 a itens de backlog em `70-operacao-governanca/03-tasks`.
- [ ] Reexecutar esta análise a cada mudança estrutural relevante (novo app, nova stack, repositório novo).
