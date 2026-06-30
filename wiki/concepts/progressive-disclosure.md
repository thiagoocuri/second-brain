---
title: "Progressive Disclosure (Skills)"
type: concept
tags: [ai, skills, contexto, tokens, eficiencia]
created: 2026-04-18
updated: 2026-04-18
sources: 1
---

## Definition

Progressive disclosure é o mecanismo pelo qual [[skills-ia]] são carregadas no [[context-window]] de forma incremental: apenas nome e descrição ficam sempre presentes no contexto; o conteúdo completo da skill só é adicionado quando o agente decide que aquela skill é necessária para a tarefa atual.

É a principal vantagem arquitetural de skills sobre arquivos de configuração estáticos (CLAUDE.md, agent.md).

## Evidence & Examples

**Fluxo de progressive disclosure** ([[claude-code-masterclass]]):

```
Contexto sempre presente:
  - skill: "code-structure"
  - description: "Use when multiple workflows duplicate the same operational logic..."
  → ~53 tokens

Quando o agente precisa da skill:
  - Conteúdo completo carregado: 116 linhas
  → ~944 tokens (só quando necessário)
```

**Comparação com agent.md:**
- Com agent.md: 944 tokens consumidos em **cada turno**, usada ou não
- Com skill: 53 tokens por turno + 944 apenas quando ativada

**Como o agente decide quando carregar a skill:**
O agente lê o nome e a descrição de todas as skills disponíveis. Quando o usuário faz uma solicitação que bate com a descrição, ele "abre" a skill e lê o conteúdo completo antes de executar.

**Implicação para escrever boas descrições de skills:**
A descrição é o único sinal que o agente tem para decidir se usa a skill. Uma descrição vaga → skill nunca ativada ou ativada nas horas erradas.

## Counter-evidence & Tensions

- Progressive disclosure depende do agente ter boa capacidade de matching entre a solicitação do usuário e a descrição da skill. Em modelos menores ou com contexto muito cheio, o matching pode falhar.

## Related Concepts

[[skills-ia]], [[context-window]], [[agentes-ia]]

## Sources

[[claude-code-masterclass]]
