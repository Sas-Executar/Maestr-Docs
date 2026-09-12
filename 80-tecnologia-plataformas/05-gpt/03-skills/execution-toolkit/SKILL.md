---
name: execution-toolkit
description: >
  Skill composta para orquestração de workflows com múltiplos agentes,
  processamento de imagens existentes e redação técnica estruturada.
  Use progressive disclosure: leia apenas a referência necessária para a tarefa.
---

# Execution Toolkit

Esta skill reúne três capacidades complementares:

1. **Workflow Composer** — decomposição e orquestração de tarefas independentes com múltiplos agentes.
2. **Image Processing** — compreensão e transformação determinística de imagens existentes.
3. **Technical Writing** — produção de relatórios, análises e documentos técnicos em Markdown.

## Progressive Disclosure

Não carregue todas as referências por padrão.

Leia primeiro apenas este arquivo e selecione a referência necessária conforme a tarefa.

| Necessidade | Referência |
|---|---|
| Planejar execução, fan-out, map/reduce ou múltiplos subagentes | `references/workflow-composer.md` |
| Entender, inspecionar ou transformar uma imagem existente | `references/image-processing.md` |
| Produzir relatório, artigo, análise ou documento técnico longo | `references/technical-writing.md` |
| Estruturar a execução antes de agir | `references/plan.md` |

## Regras de roteamento

### Workflow

Leia `references/workflow-composer.md` quando houver **3 ou mais itens independentes** e cada item exigir pesquisa, julgamento ou exploração própria.

Não use workflow para um lote puramente determinístico que possa ser executado por um único script com concorrência limitada.

### Imagens

Leia `references/image-processing.md` quando a entrada principal for uma imagem existente.

Use processamento determinístico apenas quando o resultado puder ser obtido reorganizando, analisando ou recodificando pixels existentes.

Quando for necessário criar novo conteúdo visual, restaurar, melhorar, estilizar ou editar semanticamente uma imagem, encaminhe para a skill de geração/edição de imagens.

### Redação técnica

Leia `references/technical-writing.md` quando o entregável for um documento técnico, relatório, análise ou artigo estruturado.

A versão final deve ser reescrita e não pode consistir apenas em notas intermediárias.

## Ordem recomendada

Quando mais de uma capacidade for necessária:

1. Consulte `references/plan.md`.
2. Carregue apenas as referências relevantes.
3. Execute coleta, análise ou transformação.
4. Use redação técnica apenas na etapa de síntese final, quando aplicável.

## Restrições gerais

- Prefira o caminho mais simples que preserve a qualidade do resultado.
- Não carregue referências sem necessidade.
- Não duplique instruções detalhadas no contexto principal.
- Preserve arquivos originais, salvo solicitação explícita em contrário.
- Use resultados estruturados quando houver comparação entre múltiplos itens.
