---
title: "Plan Mode"
type: concept
tags: [claude-code, workflow, producao, qualidade, planejamento]
created: 2026-05-24
updated: 2026-05-24
sources: 1
---

## Definition

Plan Mode é um estado do Claude Code onde o agente mapeia o plano completo de execução antes de escrever qualquer linha de código ou modificar qualquer arquivo. Ativado com Shift+Tab. O agente apresenta o plano; o usuário revisa, comenta e refina; só depois aprova a execução.

Análogo a um arquiteto desenhando a planta antes de começar a construção — o Claude não deve "começar a construir" antes de o plano estar aprovado.

## Evidence & Examples

**O problema que resolve** ([[michele-torti]], [[claude-code-masterclass]]):
- Sem plan mode: Claude começa a executar imediatamente, acumulando erros que se propagam. Corrigir no meio da execução é mais caro do que planejar antes.
- Com plan mode: erros de planejamento são identificados e corrigidos antes de qualquer mudança no código. "Um minuto de planejamento economiza 10 minutos de build."

**Fluxo de uso:**
1. `Shift+Tab` → Plan Mode ativado
2. Descreva a tarefa complexa
3. Claude apresenta plano completo (arquivos a criar/editar, sequência de passos, dependências)
4. Usuário revisa, adiciona comentários de refinamento
5. Usuário aprova → Claude executa o plano

**Quando usar:**
- Qualquer tarefa multi-step com interdependências
- Antes de builds que envolvem múltiplos arquivos
- Sempre que a tarefa tiver mais de 3 passos sequenciais

**Complemento do [[spec-todo-build]]:** Plan Mode é a ferramenta de interface; Spec → Todo → Build é o workflow de projeto. No workflow completo, Plan Mode é ativado para revisar o to-do de cada milestone antes de executar.

**Comparação com YOLO mode:**
- **Plan Mode**: colaborativo, revisão antes de execução. Melhor para tasks complexas ou destrutivas.
- **YOLO mode** (bypass de permissões): Claude executa tudo sem pedir aprovação. Melhor para tasks simples e bem definidas onde velocidade importa mais que supervisão.

## Counter-evidence & Tensions

- Plan Mode adiciona fricção ao workflow — para tarefas simples e repetitivas, o overhead de review do plano não vale o tempo.
- O plano apresentado pelo Claude pode parecer completo mas ainda conter premissas incorretas sobre o codebase. Plan Mode não elimina erros — apenas move-os para antes da execução, onde são mais baratos de corrigir.

## Related Concepts

[[three-layer-architecture]], [[spec-todo-build]], [[claude-md]], [[agentes-ia]]

## Sources

[[claude-code-masterclass]]
