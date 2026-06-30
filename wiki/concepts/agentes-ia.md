---
title: "Agentes de IA"
type: concept
tags: [ai, agentes, llm, automacao, produtividade]
created: 2026-04-18
updated: 2026-05-24
sources: 2
---

## Definition

Um agente de IA é um sistema que recebe um objetivo, planeja os passos necessários, e executa ações autonomamente — usando ferramentas (APIs, leitura/escrita de arquivos, envio de mensagens) para atingir o resultado sem aprovação humana a cada passo.

Diferença de um chatbot: chatbot responde. Agente **age**.

O comportamento do agente é determinado pelo seu **contexto**: sistema de prompt, arquivos de configuração, [[skills-ia]], ferramentas disponíveis e o histórico de conversa. A qualidade do output depende mais da qualidade do contexto fornecido do que do modelo em si.

## Evidence & Examples

**Composição do contexto de um agente** (Ross Mike, [[claude-code-masterclass]]):
1. **System prompt** — instruções gerais do provedor do modelo (ex: Claude Code)
2. **Agent.md / CLAUDE.md** — informações proprietárias do usuário (usar com parcimônia)
3. **Skills** — nome+descrição no contexto; conteúdo completo carregado por progressive disclosure
4. **Ferramentas (tools)** — capacidades que o harness disponibiliza (Read, Write, Bash, APIs)
5. **Codebase / arquivos** — contexto do projeto atual
6. **Conversa do usuário** — histórico da sessão

**Ciclo de construção correto** ([[claude-code-masterclass]]):
1. Identificar o workflow
2. Executar o workflow manualmente com o agente (passo a passo, turno a turno)
3. Após execução bem-sucedida, pedir ao agente para criar a skill
4. Usar a skill em produção — identificar falhas — corrigir — atualizar skill (ver [[skills-ia]])

**Aplicações para [[Avalyse]]:**
- Agente de prospecção: scraping Google Maps → Claude analisa leads → GHL dispara WhatsApp
- Agente de monitoramento: monitora novos reviews → resposta automática → relatório semanal
- Agente de onboarding: cria subconta GHL, configura integrações quando fecha cliente

**Loop de 4 passos do agente Claude Code** ([[michele-torti]], [[claude-code-masterclass]]):
1. **Entender** — lê sua mensagem + todos os arquivos de contexto ([[claude-md]], skills, histórico)
2. **Planejar** — decide o que fazer e quais ferramentas usar
3. **Usar ferramentas** — lê/escreve arquivos, roda comandos, chama APIs
4. **Output** — retorna resultados

A qualidade do output é determinada na etapa 1 (entender). Por isso [[claude-md]] e [[skills-ia]] são os principais alavancadores de qualidade — eles enriquecem o que o agente "entende" antes de planejar.

**Setup Mode vs Use Mode** ([[claude-code-masterclass]]):
| Fase | O que acontece | Erro comum |
|---|---|---|
| **Setup Mode** | Scaffolding: escrever CLAUDE.md, instalar skills, configurar MCPs, criar sub-agentes | Pular esta fase |
| **Use Mode** | Executar tarefas reais | Só fase que a maioria usa |

A maioria das pessoas vai direto ao Use Mode e depois estranha por que o Claude é inconsistente. Setup é o multiplicador. Quanto mais completo o setup, melhor cada tarefa em Use Mode.

**Modelos disponíveis e quando usar cada um** ([[claude-code-masterclass]]):
| Modelo | Perfil | Quando usar |
|---|---|---|
| Claude Haiku | Mais barato, mais rápido | Lookups simples, leitura de arquivos, transformações rápidas |
| Claude Sonnet | Balanceado (padrão) | Código, escrita, maioria das tarefas diárias |
| Claude Opus | Mais poderoso, mais caro | Debugging difícil, builds full-stack complexos, raciocínio profundo |

**Modos interativo vs headless** ([[claude-code-masterclass]]):
- **Interativo**: você está no loop, Claude pede aprovação antes de ações destrutivas
- **Headless**: Claude roda autonomamente sem prompts — usado para automação agendada e pipelines CI/CD. Requer configuração cuidadosa de permissões e [[hooks-claude]] para evitar erros silenciosos.

## Counter-evidence & Tensions

- O argumento "modelo já é bom, foque no contexto" pode subestimar casos onde o modelo genuinamente falha em raciocínio complexo. A qualidade do contexto e a capacidade do modelo são complementares, não substitutos.
- Agentes autônomos têm "blast radius" maior que chatbots — um erro de julgamento pode disparar mensagens, apagar dados, ou fazer chamadas de API com consequências reais.
- Setup Mode exige investimento upfront que pode parecer excessivo para projetos pequenos. A recompensa é não-linear: projetos simples ganham pouco; projetos complexos ou recorrentes ganham muito.

## Related Concepts

[[skills-ia]], [[context-window]], [[sub-agentes]], [[progressive-disclosure]], [[mcp]], [[claude-md]], [[hooks-claude]], [[agent-teams]], [[three-layer-architecture]]

## Sources

[[claude-code-masterclass]]
