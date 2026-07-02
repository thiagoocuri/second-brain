# Overview — Fluxo de Outbound WhatsApp v4 (Curiosity Gap + Demo Gate)

**Spec:** `docs/superpowers/specs/2026-07-01-outbound-curiosity-gap-design.md`
**Plano de execução:** `docs/superpowers/plans/2026-07-01-outbound-curiosity-gap-flow-plan.md`
**Status:** conteúdo escrito, pendente de gravação do vídeo e ativação no Bulker
**Executor:** Alex Hormozi. Todas as mensagens de exemplo neste fluxo (curiosity gap, mensagem personalizada, CTA de demo, follow-up) são rascunhos de referência — o executor tem liberdade para reescrever qualquer texto de acordo com seu próprio filtro e estilo, desde que respeite as regras transversais abaixo (gate, personalização, termos proibidos).

---

## Por que esse fluxo existe

O v3 terminava em CTA de trial self-serve, e o gargalo identificado ([[analyses/gargalo-conversao-outreach]]) era resposta → reunião: sem prova social própria, o pitch por texto frio não convence. Este fluxo troca o CTA final por uma demo obrigatória — só lá o mecanismo (avaliações, SEO, ranking no Maps) é revelado. O curiosity gap vende a *existência* do diagnóstico antes de qualquer conteúdo.

---

## Sequência completa

| Etapa | Arquivo | O que faz |
|---|---|---|
| 1. Quebra-gelo | *(reuso do v3, sem arquivo novo)* | Filtra bots, abre a conversa |
| 2. Curiosity gap | [02-curiosity-gap.md](02-curiosity-gap.md) | 2 variantes (A/B) vendendo a existência do raio-x, sem entregar nada |
| 3. Mensagem + vídeo | [03-mensagem-personalizada.md](03-mensagem-personalizada.md) · [03-video-roteiro.md](03-video-roteiro.md) | Texto personalizado (nome/nicho) + vídeo fixo genérico mostrando takeaways, não o mecanismo |
| 4. CTA de demo (gate) | [04-cta-demo.md](04-cta-demo.md) | Convite pra demo + scripts de recusa quando o lead pede o diagnóstico por texto |
| 5. Follow-up | [05-followup-cold-call.md](05-followup-cold-call.md) | Sem resposta em 24-48h → escala para ligação (decisão de 2026-07-01) |

---

## Regras que atravessam todas as etapas

- Nunca mencionar "avaliação", "review" ou "SEO" antes da demo.
- Nenhum dado real do diagnóstico (ranking, nota, pontos específicos) sai por texto — só na demo, ao vivo.
- Personalização (`{Nome}`, `{Negocio}`) só no texto que acompanha o vídeo — o vídeo em si é único e reaproveitável.
- Segmentação e ICP não mudam ([[concepts/tracks-prospecao]], [[concepts/perfil-de-cliente-ideal]]) — este fluxo altera só a sequência de mensagens e o CTA.

## Em aberto

- Variante vencedora do passo 2 (A vs B) — decide-se rodando o teste, não por design.
- Cold call como canal de entrada próprio (Track 2) fica para Fase 2 — aqui ele entra só como follow-up de reengajamento.
