---
title: "MCP (Model Context Protocol)"
type: concept
tags: [claude-code, protocolo, plugins, integracao, ferramentas]
created: 2026-05-24
updated: 2026-05-24
sources: 1
---

## Definition

MCP (Model Context Protocol) é o padrão de plugins que expande as capacidades nativas do Claude Code além das ferramentas built-in (leitura de arquivos, escrita, bash). Cada MCP conecta o agente a um sistema externo — browser, banco de dados, API — e adiciona novas ações disponíveis na sessão.

Configurado em `.mcp.json` na raiz do projeto. Carregado automaticamente ao iniciar uma sessão — com custo fixo de tokens independentemente de ser usado ou não.

## Evidence & Examples

**Dois MCPs essenciais** (segundo [[michele-torti]], [[claude-code-masterclass]]):

| MCP | Capacidade adicionada | Uso principal |
|---|---|---|
| **Chrome DevTools MCP** | Controle total do browser: clicar, preencher forms, navegar, screenshot | Automação web, testes visuais, scraping |
| **Supabase MCP** | Conexão com banco vetorial Supabase: busca semântica, dados persistentes, RAG | Memória de longo prazo, busca inteligente |

**Custo de contexto:**
Carregar 2 MCPs consome ~10.800 tokens automaticamente — ainda antes de qualquer mensagem. Isso é ~5% de um [[context-window]] de 200k tokens, mas pode se acumular com outros elementos.

**Regra prática** ([[claude-code-masterclass]]): use no máximo 2–3 MCPs simultâneos. Quando um MCP se torna estável e você usa suas funções de forma previsível, converta-o em uma [[skills-ia]] — o agente aprende a usar a API diretamente, sem o overhead do MCP.

**Onde encontrar:** mcp-servers.org agrega MCPs disponíveis por categoria.

## Counter-evidence & Tensions

- O custo fixo de tokens de MCPs penaliza sessões curtas — você paga os ~10.800 tokens mesmo que não use o MCP naquela conversa. Para workflows que raramente precisam do browser ou do banco, pode ser mais eficiente acionar manualmente do que deixar o MCP sempre carregado.
- MCPs de terceiros têm os mesmos riscos de segurança que [[skills-ia]] de terceiros — um MCP malicioso tem acesso às ferramentas que você autorizou.

## Related Concepts

[[skills-ia]], [[context-window]], [[agentes-ia]], [[claude-md]], [[hooks-claude]]

## Sources

[[claude-code-masterclass]]
