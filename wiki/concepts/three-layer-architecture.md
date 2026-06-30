---
title: "Three-layer Architecture"
type: concept
tags: [claude-code, arquitetura, workflow, estrutura, agentes]
created: 2026-05-24
updated: 2026-05-24
sources: 1
---

## Definition

Framework estrutural de [[michele-torti]] para organizar projetos de automação com Claude Code. Divide o projeto em 3 camadas hierárquicas com responsabilidades distintas, prevenindo o problema de degradação exponencial de precisão em chains de prompts (fórmula 0.9^5 = 59%).

Com estrutura clara, o Claude sabe onde colocar cada coisa e se recupera de erros de forma previsível — em vez de decidir ad-hoc onde salvar outputs ou como lidar com exceções.

## Evidence & Examples

**As 3 camadas** ([[claude-code-masterclass]]):

| Camada | Pasta | Conteúdo | Responsabilidade |
|---|---|---|---|
| **1 — Directives** | `directives/` | SOPs, markdowns, `spec.md` | Dizer ao Claude *o que* fazer: objetivos, inputs/outputs, ferramentas, edge cases |
| **2 — Orchestration** | `orchestration/` | Lógica LLM, roteamento, error handling | Onde o raciocínio do agente vive: como lidar com erros, qual sub-agente acionar, self-healing |
| **3 — Execution** | `execution/` | Scripts Python, chamadas de API, processamento de dados | O código que realmente executa: sem lógica de decisão aqui |

**Analogia:** Directives = manual de operações de uma empresa. Orchestration = gerente que interpreta o manual e distribui tarefas. Execution = funcionários que executam as tarefas.

**Por que previne o problema 0.9^5:**
Sem estrutura, erros em qualquer passo se propagam para os seguintes sem ponto de recuperação. Com as 3 camadas, a Orchestration tem um lugar definido para detectar e corrigir erros antes de passar para Execution — o agente sabe onde olhar para recuperar.

**Aplicação prática** ([[claude-code-masterclass]]):
- Antes de qualquer build, `CLAUDE.md` com as 3 camadas é criado primeiro
- `spec.md` vive em `directives/` e serve de fonte de verdade para todo o build
- Scripts de API e processamento ficam em `execution/`, isolados da lógica de decisão

## Counter-evidence & Tensions

- Para projetos muito simples (script único, tarefa pontual), a overhead da arquitetura em 3 camadas pode não valer o esforço. O framework foi desenhado para workflows recorrentes e agents em produção.
- A separação entre Orchestration e Execution pode ser subjetiva — onde termina a "lógica de decisão" e começa a "execução" nem sempre é claro, especialmente em scripts que tomam decisões simples.

## Related Concepts

[[claude-md]], [[agentes-ia]], [[spec-todo-build]], [[plan-mode]], [[sub-agentes]]

## Sources

[[claude-code-masterclass]]
