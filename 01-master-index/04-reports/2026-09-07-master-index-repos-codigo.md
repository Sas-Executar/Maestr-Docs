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
---

# Master Index · Repositórios de Código do Ecossistema Sas-Executar

Consolida a análise individual dos 6 repositórios GitHub do ecossistema, sob a governança das skills **testing-strategy** (estratégia e cobertura de testes) e **code-review** (qualidade, CI e higiene de revisão). Cada repositório recebeu, na branch `claude/plugin-engineer-workflow-klbtix`, um documento de análise individual referenciado na seção 4.

## 1. Escopo e confirmação de acesso

| Repositório | Acesso confirmado | Branch padrão | Estado do repositório |
|---|---|---|---|
| `Sas-Executar/Sas-Executar` | ✅ leitura + escrita | `main` | Ativo, 30 branches (28 dependabot) |
| `Sas-Executar/CustoCognitivoBlog` | ✅ leitura + escrita | `main` | Ativo, 24 branches, alta velocidade de iteração |
| `Sas-Executar/Desyng-System-ecossitema.` | ✅ leitura + escrita | ⚠️ sem `main` (usa `claude/design-handoff-specs-ulc1r1`) | Ativo, especificação sem `main` promovido |
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

A partir disso, cada repositório foi posicionado em uma hierarquia única de maturidade de arquitetura/desenvolvimento.

## 3. Hierarquia de arquitetura e desenvolvimento — do mais ao menos desenvolvido

| # | Repositório | Categoria | Sinais de maturidade | Sinais de lacuna |
|---|---|---|---|---|
| 1 | **Sas-Executar/Sas-Executar** | Produto (SaaS canônico) | Turborepo+Bun, Biome, Playwright E2E com **gate de performance**, Vitest, IaC AWS (OIDC, sem credenciais estáticas), apps web+mobile (Expo/Tamagui), release semântico automatizado, `AGENTS.md` | Cobertura de teste não quantificada; `apps/mobile` sem gate de teste declarado; alto volume de PRs dependabot pendentes de triagem |
| 2 | **Sas-Executar/CustoCognitivoBlog** | Produto (CMS + Site) | pnpm monorepo, Next.js16+Payload3 e Astro, fronteira de tipos (`cms-types`), feature flag para rollout controlado (RC Scanner), CI configurado, documentação de arquitetura e migração viva | Sem test runner/pasta de testes visível na raiz; migração Astro sem gate de paridade; branches de feature acumuladas sem limpeza |
| 3 | **Sas-Executar/Desyng-System-ecossitema.** | Especificação / handoff | Governança de decisão formalizada (`SOT_RESOLUTION.md`, `OPEN_QUESTIONS.md`), plano de implementação faseado, rastreabilidade de fontes (ADRs, packs visuais) | Zero código de aplicação em execução (por design); sem branch `main` promovida; sem mecanismo de conformidade automatizada com os consumidores |
| 4 | **Sas-Executar/Cognitivo-Mapa** | Produto (landing standalone) | Código de aplicação real **em produção**; contrato de dados versionado (`consultation-schema.json`); governança de claims editoriais | Sem build tooling, lint, teste ou CI; gaps de qualidade (Core Web Vitals, WCAG 2.2) autodeclarados no README |
| 5 | **Sas-Executar/Maestr-Docs** | Governança / conhecimento | Taxonomia de 14 domínios + registro central de Folder IDs (`CENTRAL_CONTROL.csv`), workflow de intake→classificação→canônico, submódulo git para skills Anthropic | Não é software executável — não se aplica CI/teste de código; depende de disciplina manual para manter o CSV sincronizado |
| 6 | **Sas-Executar/programa-sas** | Não inicializado | — | Repositório vazio: sem commits, sem branches, sem conteúdo a avaliar |

**Leitura da hierarquia:** os níveis 1–2 são produtos com código executável e engenharia madura; o nível 3 é um contrato de especificação que alimenta os níveis 1–2; o nível 4 é software real porém sem disciplina de engenharia; o nível 5 é infraestrutura de conhecimento (nenhum código para testar, por desenho); o nível 6 ainda não existe como projeto.

## 4. Análises individuais (link canônico)

| Repositório | Documento |
|---|---|
| Sas-Executar/Sas-Executar | `docs/governance/2026-09-07-repo-analysis-plugin-engineer.md` (branch `claude/plugin-engineer-workflow-klbtix`) |
| Sas-Executar/CustoCognitivoBlog | `docs/governance/2026-09-07-repo-analysis-plugin-engineer.md` (branch `claude/plugin-engineer-workflow-klbtix`) |
| Sas-Executar/Desyng-System-ecossitema. | `docs/governance/2026-09-07-repo-analysis-plugin-engineer.md` (branch `claude/plugin-engineer-workflow-klbtix`) |
| Sas-Executar/Cognitivo-Mapa | `docs/2026-09-07-repo-analysis-plugin-engineer.md` (branch `claude/plugin-engineer-workflow-klbtix`) |
| Sas-Executar/Maestr-Docs | este documento |
| Sas-Executar/programa-sas | `docs/governance/2026-09-07-repo-analysis-plugin-engineer.md` (repositório inicializado nesta mesma rodada — ver seção 6) |

## 5. Relações entre repositórios

```
Desyng-System-ecossitema. (spec/tokens)
        │  fonte-da-verdade visual
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

## 6. Recomendações de governança priorizadas

1. **programa-sas**: definir o propósito do repositório (produto novo? extração de módulo existente?) antes de qualquer código ser adicionado — hoje ele não tem escopo declarado em lugar nenhum do ecossistema.
2. **Desyng-System-ecossitema.**: promover `claude/design-handoff-specs-ulc1r1` a `main` para dar ao repositório uma base estável de revisão.
3. **Sas-Executar/Sas-Executar**: triagem semanal das branches `dependabot/*` e definição de gate de teste para `apps/mobile`.
4. **CustoCognitivoBlog**: gate de paridade E2E para a migração Astro e limpeza de branches de feature já mescladas.
5. **Cognitivo-Mapa**: CI mínimo (lint + validação de schema) e teste automatizado de Core Web Vitals/acessibilidade, dado que os próprios gaps já estão documentados no README.
6. **Maestr-Docs**: manter esta seção de `04-reports` como o índice mestre vivo — cada nova análise de repositório deve ser adicionada aqui, não substituída.

## 7. Próximos passos

- [ ] Abrir PR (draft) em cada um dos 6 repositórios a partir da branch `claude/plugin-engineer-workflow-klbtix`.
- [ ] Revisar e, quando aprovado, promover as recomendações da seção 6 a itens de backlog em `70-operacao-governanca/03-tasks`.
- [ ] Reexecutar esta análise a cada mudança estrutural relevante (novo app, nova stack, repositório novo).
