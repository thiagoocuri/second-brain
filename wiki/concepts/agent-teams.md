---
title: "Agent Teams"
type: concept
tags: [claude-code, multi-agent, orquestracao, paralelizacao, custo]
created: 2026-05-24
updated: 2026-05-24
sources: 1
---

## Definition

Agent Teams são configurações multi-agente onde cada membro tem seu próprio [[context-window]] independente e pode se comunicar diretamente com outros membros da equipe. Diferem de [[sub-agentes]]: sub-agentes compartilham o contexto do agente principal e seus resultados retornam apenas ao pai; agent teams têm contextos isolados e comunicação lateral entre si.

Habilitado via `{ "enableAgentTeams": true }` em `settings.json` do projeto.

## Evidence & Examples

**Quando usar Agent Teams vs Sub-agentes** ([[michele-torti]], [[claude-code-masterclass]]):

| Cenário | Use | Motivo |
|---|---|---|
| Tarefas independentes em paralelo (LinkedIn + blog post) | Sub-agentes | Mais barato; sem necessidade de coordenação |
| Tarefas interdependentes (front end + back end + testes) | Agent Teams | Agentes precisam compartilhar outputs intermediários |
| Migração de múltiplos serviços simultâneos | Agent Teams | Coordenação essencial entre serviços |
| Processamento de batch (84 emails em 4 grupos) | Sub-agentes | Items independentes; paralelização simples |

**Exemplo de pipeline de vendas** (4 agentes, [[claude-code-masterclass]]):
1. **Insights Agent** — lê transcrição de discovery call → extrai overview, dores, timeline, red flags → output: `client-summary.md`
2. **Proposal Builder** *(paralelo com CRM Agent)* — lê `client-summary.md` → output: `product-proposal.md`
3. **CRM Agent** *(paralelo com Proposal Builder)* — lê `client-summary.md` → output: JSON para atualização de CRM
4. **Follow-up Email Agent** — lê outputs dos agentes 2 e 3 → escreve email de follow-up

Agents 2 e 3 aguardam o Agent 1; Agent 4 aguarda os Agents 2 e 3. Tempo total: ~2 minutos em vez de 6 (redução de ~66%).

**Custo real documentado** ([[claude-code-masterclass]]): ~$80 em uma build complexa com 4 agentes usando Claude Opus. Cada agente tem seu próprio contexto — você paga N sessões de Claude em paralelo.

**Vantagem de paralelização**:
- Tradicional: 6 tarefas × 1 minuto = 6 minutos
- Agent Team com 3 workers: 6 ÷ 3 = 2 minutos
- Para workflows complexos: redução de horas para minutos

## Counter-evidence & Tensions

- O custo de ~$80/build complexa pode ser proibitivo no estágio inicial da [[Avalyse]]. A maioria dos casos de uso de uma startup early-stage é coberta por [[sub-agentes]] a fração do custo.
- Agent Teams aumentam drasticamente a complexidade de debugging — quando um agente falha, rastrear qual e por quê exige logs cuidadosos de cada contexto independente.
- [[sub-agentes]] têm limitação oposta: não podem se comunicar entre si — resultados sempre passam pelo agente principal. Para tasks onde o output de A informa B, agent teams são necessários, mas o custo deve justificar.

## Related Concepts

[[sub-agentes]], [[agentes-ia]], [[context-window]], [[claude-md]]

## Sources

[[claude-code-masterclass]]
