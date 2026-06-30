---
title: "CLAUDE.md"
type: concept
tags: [claude-code, configuracao, memoria, setup, agentes]
created: 2026-05-24
updated: 2026-05-24
sources: 1
---

## Definition

CLAUDE.md é o arquivo de configuração central de um projeto Claude Code. Funciona como o "cérebro" do agente: contém tudo que o Claude precisa saber sobre o projeto para não precisar perguntar. É carregado automaticamente no contexto em **todo turno de conversa** — diferente de [[skills-ia]], que usam [[progressive-disclosure]] e só carregam quando necessárias.

Existe em dois níveis:
- **Global** (`~/.claude/CLAUDE.md`): aplica-se a todos os projetos
- **Projeto** (raiz do projeto): sobrescreve o global para o projeto específico

## Evidence & Examples

**5 seções recomendadas por [[michele-torti]]** ([[claude-code-masterclass]]):
1. **Contexto do projeto** — o que é, qual problema resolve, stack principal
2. **Arquitetura** — estrutura de pastas, padrões de código, decisões de design
3. **Workflows principais** — como executar tarefas comuns (build, test, deploy)
4. **Decisões de design** — por que certas escolhas foram feitas (evita que o Claude "desfaça" decisões intencionais)
5. **Contexto importante** — armadilhas, quirks de APIs, convenções de nomes, o que NÃO fazer

**Como CLAUDE.md se compara a outras formas de persistência:**
| Mecanismo | Quando carrega | Custo de tokens | Caso de uso |
|---|---|---|---|
| CLAUDE.md | Todo turno | Alto (linear com tamanho) | Regras e contexto sempre relevantes |
| [[skills-ia]] | Só quando relevante | Baixo (~53 tokens idle) | Workflows específicos e ocasionais |
| Agent memory | Na abertura da sessão | Médio | Preferências e feedback acumulado do sub-agente |

**CLAUDE.md como memória permanente** ([[claude-code-masterclass]]):
Em vez de repetir em toda sessão "responda sempre em português, máximo 150 palavras, nunca use travessão", codifique uma vez no CLAUDE.md e aplica para sempre. Cada regra que você digitaria mais de uma vez pertence aqui.

**Geração automática:**
O comando `/init` analisa o projeto atual e gera um CLAUDE.md base. Ponto de partida — não substitui refinamento manual iterativo.

## Counter-evidence & Tensions

- CLAUDE.md é carregado em **todo turno** — um arquivo de 1.000 linhas (~7.000 tokens) desperdiça esse espaço mesmo quando o conteúdo não é relevante para a tarefa atual. Regra prática: mantenha o CLAUDE.md enxuto; mova workflows específicos para [[skills-ia]].
- Informação no CLAUDE.md não garante que o Claude a seguirá em contextos muito longos — quanto mais cheio o [[context-window]], maior o risco do agente "esquecer" instruções do início do contexto.

## Related Concepts

[[skills-ia]], [[context-window]], [[progressive-disclosure]], [[agentes-ia]], Setup Mode, [[hooks-claude]]

## Sources

[[claude-code-masterclass]]
