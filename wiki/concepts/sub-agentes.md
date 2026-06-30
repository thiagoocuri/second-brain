---
title: "Sub-agentes"
type: concept
tags: [ai, agentes, multi-agent, orquestracao, produtividade]
created: 2026-04-18
updated: 2026-05-24
sources: 2
---

## Definition

Sub-agentes são agentes especializados orquestrados por um agente principal. O agente principal recebe objetivos de alto nível e delega partes do trabalho para sub-agentes com contexto e [[skills-ia]] específicas para cada domínio.

## Evidence & Examples

**Quando sub-agentes fazem sentido** ([[claude-code-masterclass]]):
- Quando você já tem workflows bem definidos e skills estabilizadas para o domínio
- Quando o agente principal claramente "não deveria" fazer determinado tipo de trabalho (ex: análise financeira vs. geração de conteúdo)
- Quando o volume de tarefas em um domínio justifica especialização

**Sequência correta de escala** (Ross Mike):
1. Comece com **1 agente** fazendo tudo
2. Construa [[skills-ia]] para seus workflows principais
3. Quando um workflow tiver skills estabilizadas e volume suficiente → crie um sub-agente
4. O agente principal gerencia os sub-agentes

**Exemplo real** (Ross Mike, canal do YouTube):
- Agente principal gerencia e orquestra
- Sub-agente de marketing: análise de sponsors, relatórios de performance
- Sub-agente de negócios: contratos, finanças
- Sub-agente pessoal: agenda, emails

**Erro comum:** criar 10–15 sub-agentes antes de ter workflows definidos. Sub-agentes sem skills e contexto de execução real geram resultados piores que 1 agente bem construído.

**Criação de sub-agentes** ([[michele-torti]], [[claude-code-masterclass]]):
- **Automático**: `/agents` (terminal) — walk-through interativo: nome, descrição, modelo, ferramentas, cor, memória
- **Manual**: criar `.claude/agents/<nome-do-agente>.md` com os campos:
  - `name` — como referenciar o agente
  - `description` — quando o Claude deve usar este agente (Claude lê isso para rotear tarefas automaticamente)
  - `tools` — nível de permissão (read-only / balanced / full)
  - `model` — haiku/sonnet/opus
  - `memory: project` — habilita memória persistente entre sessões

**Níveis de permissão:**
| Nível | Ferramentas disponíveis | Quando usar |
|---|---|---|
| Read-only | ler, grep, glob | Pesquisa que não deve modificar nada |
| Balanced | ler, editar, bash, grep, glob | Maioria dos workflows; não apaga arquivos |
| Full | tudo (campo `tools` omitido) | Tasks bem definidas, estruturadas, baixo risco |

**Memória persistente de sub-agentes** ([[claude-code-masterclass]]):
Sub-agentes começam do zero a cada sessão. Com `memory: project`, o Claude cria `.claude/agent_memory/memory.md` e escreve feedback, tom e preferências nele. A cada nova sessão, o agente lê sua memória primeiro. Loop: executar tarefa → Claude escreve memória → próxima sessão lê memória → output melhora. Sub-agentes auto-aprimoráveis.

**Trigger de sub-agentes** ([[claude-code-masterclass]]):
1. Linguagem natural ("use o code reviewer para verificar minhas mudanças")
2. @mention (`@email-writer Escreva um email para...`) — garante o acionamento; recomendado quando há múltiplos agentes com responsabilidades sobrepostas
3. Session-wide (`//agent code-reviewer`) — bloqueia toda a sessão em um único agente

**Limitação crítica:** sub-agentes *não se comunicam entre si*. Resultados sempre retornam ao agente principal. Para tasks onde o output de um agente informa outro, use [[agent-teams]] — a custo maior.

**Paralelização por batch** ([[claude-code-masterclass]]): 84 emails divididos em 4 sub-agentes (1–20, 21–40, 41–60, 61–84), todos rodando simultaneamente. Para milhares de items, reduz horas para minutos — desde que os items sejam independentes entre si.

## Counter-evidence & Tensions

- A orquestração de múltiplos agentes aumenta a complexidade e os pontos de falha. Cada sub-agente é um contexto separado — informações podem se perder na comunicação entre eles.
- Para a maioria dos casos de uso de uma pessoa (ou empresa pequena), 1 agente bem configurado com boas skills supera sistemas multi-agente mal construídos.
- Sub-agentes compartilham o [[context-window]] da conversa principal — não têm contexto isolado. Isso os diferencia de [[agent-teams]], onde cada membro tem seu próprio contexto independente.

## Related Concepts

[[agentes-ia]], [[skills-ia]], [[context-window]], [[agent-teams]], [[claude-md]]

## Sources

[[claude-code-masterclass]]
