---
title: "Context Window"
type: concept
tags: [ai, llm, contexto, performance, tokens]
created: 2026-04-18
updated: 2026-05-24
sources: 2
---

## Definition

O context window é o espaço total de informação que um modelo de linguagem pode "ver" durante uma conversa ou execução. Tudo que o agente sabe — system prompt, histórico de conversa, arquivos lidos, skills carregadas, resultados de ferramentas — ocupa espaço nessa janela.

A janela é medida em **tokens** (aproximadamente: 1 token ≈ 0,75 palavras em inglês). Modelos atuais têm janelas de 100k–200k tokens, mas performance degrada à medida que a janela se enche.

## Evidence & Examples

**Zona de performance ótima** ([[claude-code-masterclass]]):
- 0–70% da janela: modelo performa bem
- 70–80%: degradação começa
- 90–100%: modelo "fica burro" — perde coerência, ignora instruções anteriores, comete erros básicos

**Composição típica do context window de um agente:**
| Elemento | Tokens (estimativa) |
|---|---|
| System prompt do provedor | ~2.000–5.000 |
| CLAUDE.md (se usado) | 500–7.000+ |
| Skills (nome+descrição cada) | ~50–100 por skill |
| Skill carregada completa | 200–2.000 |
| Histórico de conversa | cresce continuamente |
| Arquivos/código lidos | variável |

**Implicação prática para gerenciamento:**
- Um CLAUDE.md de 1.000 linhas (~7.000 tokens) gasta esse espaço em **todo turno**
- A mesma informação como [[skills-ia]] gasta ~53 tokens por turno (só nome+descrição)
- Quando o contexto fica muito cheio, ferramentas como Claude Code fazem **compactação automática** do histórico

**Analogia humana** (Ross Mike): É como estudar na última hora para uma prova. Se você joga toneladas de informação numa sessão, o desempenho cai. O mesmo vale para o modelo — mais informação não é sempre melhor.

**Claude Code: 200k tokens por conversa** ([[michele-torti]], [[claude-code-masterclass]]):
Cada mensagem enviada, cada resposta do Claude, cada arquivo lido, cada tool call ocupa espaço nessa janela. Quando cheia, a performance degrada. Regra: trate como um caderno de 200k páginas — não desperdice com conteúdo irrelevante.

**Kitchen Sink vs Clean Session** ([[claude-code-masterclass]]):
- **Kitchen Sink**: uma sessão longa com todo o contexto do projeto carregado — útil quando tudo está relacionado. Custo: 42% do contexto numa mesma tarefa.
- **Clean Session**: conversa nova para cada tarefa não relacionada — 9% de contexto na mesma tarefa. Regra: inicie nova conversa ao trocar de tarefa não relacionada.

**Ferramentas de gerenciamento de contexto no Claude Code** ([[claude-code-masterclass]]):

| Comando | Efeito | Quando usar |
|---|---|---|
| `/compact` | Comprime conversa em resumo, libera ~180k tokens mantendo estado | Chat ficou longo mas quer continuar na mesma sessão |
| `/clear` | Reset completo, começa do zero | Tarefa completamente diferente |
| `/context` | Mostra breakdown de uso: system prompt, tools, memória, skills, mensagens, espaço livre | Antes de tasks longas, para monitorar degradação |

**Custo de MCPs no contexto** ([[claude-code-masterclass]]): carregar 2 [[mcp|MCPs]] consome ~10.800 tokens automaticamente — ainda antes de qualquer mensagem. Limite recomendado: 2–3 MCPs simultâneos.

**Fórmula 0.9^5 e o contexto** ([[claude-code-masterclass]]): separar chains de prompts em conversas independentes não só reseta o erro acumulado — também reseta o contexto, garantindo que o Claude começa cada passo com janela limpa.

## Counter-evidence & Tensions

- Modelos estão melhorando a tolerância a contextos longos a cada geração — o ponto de degradação tende a subir. A regra dos 70% é heurística, não lei.
- Algumas tarefas (análise de documentos longos, refatoração de codebase grande) exigem contexto denso. O custo de desempenho pode valer o benefício de ter toda a informação disponível.
- `/compact` preserva o estado mas perde granularidade — detalhes de passos anteriores podem sumir no resumo comprimido, causando inconsistências sutis.

## Related Concepts

[[agentes-ia]], [[skills-ia]], [[progressive-disclosure]], [[claude-md]], [[mcp]], [[agent-teams]]

## Sources

[[claude-code-masterclass]]
