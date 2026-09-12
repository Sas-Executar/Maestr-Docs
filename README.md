# sas-executar-maestro · transição em revisão

## 1. Propósito
OPERAR: agents, skills, prompts, workflows, plugins, MCP, tools, evals e specialties. Nome atual: `Maestr-Docs`. O nome alvo ainda não foi aplicado.

## 2. Não é
Documentação geral de negócio, produto e governança deve passar pela entrada do Governance.

## 3. Source of Truth
Os pacotes operacionais continuam nos caminhos existentes sob 80-tecnologia-plataformas/05-gpt. Os novos diretórios são entradas de navegação; não são cópias concorrentes.

## 4. Relação entre repositórios
Governance → Blueprints → Ecosystem. Maestro atua transversalmente.

- [Maestro](https://github.com/Sas-Executar/Maestr-Docs): OPERAR.
- [Blueprints](https://github.com/Sas-Executar/Executar-app-Blueprint): ESPECIFICAR.
- [Governance](https://github.com/Sas-Executar/Programa-Sas): GOVERNAR.
- [Ecosystem](https://github.com/Sas-Executar/next-forge): IMPLEMENTAR + RELEASE.

## 5. Estrutura
- `00-manifest/`
- `10-agents/`
- `20-skills/`
- `30-prompts/`
- `40-workflows/`
- `50-plugins/`
- `60-mcp/`
- `70-tools/`
- `80-specialties/`
- `90-evals/`
- `99-archive/`

As estruturas anteriores são preservadas durante a transição. Diretórios novos não promovem artefatos a canônicos automaticamente.

## 6. Workflow
Entrada → inventário → trabalho em branch → validação → PR → decisão explícita → merge → atualização dos índices.

## 7. Estados
`draft ≠ review ≠ approved ≠ implemented ≠ tested ≠ verified ≠ released`. Preservar também pre_approved, accepted e demais estados encontrados. `registered`, `registered_reference`, `registered_from_source` e `registered_analysis` não significam implementação. A classificação de proveniência não altera a classificação das afirmações da fonte.

## 8. Contribuição
Usar migration/*, blueprint/*, wf/*, integration/*, fix/* ou release/*. Branch representa trabalho. main é o estado-alvo canônico após aprovação e integração explícitas. Se main não existir, a branch default observada não comprova aprovação. Não reescrever histórico ou remover fontes durante a migração.

## 9. Traceability
Origem repo/branch/SHA/path → ID → requisito → AC → target → teste/evidência → release. Campos desconhecidos: GAP; owner desconhecido fica vazio. PROPOSED não é requisito existente.

## 10. Migration status
PASS_WITH_GAPS: estrutura em revisão, fontes preservadas. Renomeação, absorções, redistribuição e archive pendentes. A cópia documental do Maestro está nos PRs 2–4 do Programa-Sas; verificação de bytes não é aprovação documental.

[README anterior](00-manifest/README_BEFORE_MIGRATION.md) preservado como snapshot de referência com caminhos relativos do contexto original.
