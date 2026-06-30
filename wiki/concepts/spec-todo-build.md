---
title: "Spec → Todo → Build"
type: concept
tags: [claude-code, workflow, producao, qualidade, planejamento]
created: 2026-05-24
updated: 2026-05-24
sources: 1
---

## Definition

Workflow de milestone de [[michele-torti]] para builds complexas com Claude Code. Em vez de pedir "construa X", o usuário divide o projeto em 3 fases iterativas — spec, to-do por milestone, execução — repetindo o ciclo para cada milestone antes de avançar.

Mais tempo no planejamento; 10× melhor na execução.

## Evidence & Examples

**O workflow em 5 passos** ([[claude-code-masterclass]]):

1. **Nunca diga "construa X"** — prompts abertos sem estrutura levam a outputs inconsistentes
2. **Peça um `spec.md`** — Claude escreve um documento com: requisitos funcionais, stack de tecnologia, lista de milestones em sequência lógica. Salvo em `directives/` (ver [[three-layer-architecture]])
3. **To-do do milestone 1** — Claude gera lista de tarefas atômicas *apenas para o milestone 1*. Não gere to-do de todo o projeto de uma vez — contexto e requisitos mudam entre milestones
4. **Build do milestone 1** — execute as tarefas, use [[plan-mode]] para tasks complexas dentro do milestone
5. **Repita** — com o milestone 1 entregue e validado, gere o to-do do milestone 2 e construa. Cada iteração parte de um estado real do projeto, não de suposições feitas no início

**Por que funciona contra o problema 0.9^5:**
Cada milestone é uma conversa separada (ou pelo menos um contexto limpo) — o erro não propaga de milestone em milestone. O Claude começa cada fase com estado real do projeto, não com suposições do spec original.

**Aplicação para [[Avalyse]]:**
Qualquer feature nova (ex: módulo de relatórios, integração com nova API) deve começar com `spec.md` antes de qualquer código. Define o que é "feito" antes de começar — evita scope creep e retrabalho.

## Counter-evidence & Tensions

- Para tarefas simples (ajuste de layout, correção de bug pontual), o overhead do spec + to-do é excessivo. O workflow é desenhado para features novas e builds de médio/grande porte.
- `spec.md` pode ficar desatualizado rapidamente se os requisitos mudarem durante o build — exige discipline de atualizar o spec quando o plano muda, não apenas o código.

## Related Concepts

[[plan-mode]], [[three-layer-architecture]], [[claude-md]], [[agentes-ia]]

## Sources

[[claude-code-masterclass]]
