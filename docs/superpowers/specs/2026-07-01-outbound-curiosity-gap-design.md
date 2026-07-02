# Fluxo de Outbound — Curiosity Gap + Demo Gate

**Data:** 2026-07-01
**Status:** aprovado para Fase 1 (WhatsApp); Fase 2 (cold call) em espera
**Contexto relacionado na wiki:** [[concepts/outreach]], [[concepts/tracks-prospecao]], [[analyses/gargalo-conversao-outreach]], [[analyses/metricas-execucao-avalyse]]

---

## Racional

O funil v3 (WhatsApp) atual termina em CTA de trial self-serve, e a análise do gargalo já diagnosticou que a queda ocorre depois da resposta: sem prova social própria, o pitch por texto frio não gera credibilidade suficiente para converter resposta em ação.

Este redesenho troca o CTA final de "confia e assina" por "vem ver com seus próprios olhos". A demo passa a ser o único lugar onde o mecanismo (avaliações do Google, SEO, ranking no Maps) é revelado — quem fecha a credibilidade é o founder ao vivo, não a mensagem escrita.

O curiosity gap substitui a entrega direta do diagnóstico: em vez de soltar o lead magnet na primeira mensagem, vende-se a *existência* do diagnóstico. Isso filtra quem não tem curiosidade mínima e aumenta o valor percebido do que será entregue na demo (reciprocidade mais forte).

---

## Escopo desta versão

**Fase 1 (agora):** sequência completa via WhatsApp.
**Fase 2 (depois, fora de escopo aqui):** versão falada do curiosity gap para cold call — como canal próprio (Track 2, reviews negativos) e como escalada de follow-up.

Segmentação e ICP (Sweet Spot, tracks 1A/1B/2 — ver [[concepts/tracks-prospecao]] e [[concepts/perfil-de-cliente-ideal]]) não mudam. Este desenho altera apenas a sequência de mensagens e o mecanismo de CTA, não o targeting.

---

## Sequência WhatsApp (Fase 1)

```
1. Quebra-gelo (igual ao v3 — 3 variantes anti-ban)
        ↓ (resposta)
2. Perguntas de contexto + curiosity gap
   "Tenho um raio-x do Google de vocês que separei — achei
   interessante. Faz sentido eu te mostrar?"
        ↓ (resposta positiva)
3. Mensagem personalizada (nome + nicho do negócio) + vídeo fixo
   anexado no mesmo envio
        ↓ (resposta)
4. CTA de demo (gate rígido)
        ↓ sem resposta
5. Follow-up — EM ABERTO (ver Questões Abertas)
```

### Passo 2 — detalhe em aberto

Ainda não decidido se a mensagem abre com uma pergunta de contexto ("qual o maior desafio de vocês hoje com clientes?") antes do gap, ou vai direto para o gap. Resolver via teste A/B na prática, não bloqueia o resto do fluxo.

### Passo 3 — vídeo fixo

O vídeo é único e reaproveitável (não personalizado por lead) — só a mensagem de texto que o acompanha é personalizada (nome, nicho). Conteúdo do vídeo:

- Foca em **takeaways/outcomes**, não no mecanismo: menciona que existe um "raio-x do Google", site gratuito, pontos de melhora — sem entrar em avaliações, SEO técnico ou como o ranking funciona.
- Visual dinâmico (não é lista de texto) — motivo de ser vídeo em vez de mensagem longa.

### Passo 4 — regra do gate (sem excepção)

Nenhuma informação do diagnóstico completo (ranking, SEO, site, bullet points) sai fora da demo. Se o lead pedir "manda por mensagem", a resposta reforça o valor de ver ao vivo e mantém o convite de demo em aberto — sem ceder versão reduzida por texto. Protege contra o padrão já observado no funil anterior ("enrolando" após receber diagnóstico sem compromisso).

---

## Cold call (Fase 2 — desenhado, não priorizado)

```
Abertura (gap de confiança em 7s — Status+Alignment+Credibility+Intrigue)
        ↓
"Separei um raio-x do Google de vocês, achei interessante o que encontrei.
Consigo te mostrar numa call rápida de 10 minutos — quando fica bom pra você?"
        ↓
Fecha demo direto na ligação (sem intermediário)
```

Dois papéis no fluxo completo (quando priorizado): canal de entrada próprio (Track 2) e escalada de follow-up quando o WhatsApp não responde após o vídeo. Mesma mecânica de gap de confiança em ambos, muda só o contexto de abertura.

---

## Fora de escopo deste desenho

- Reescrita do script da demo — fica para depois; registrado apenas que a demo agora abre com apresentação do diagnóstico (5-6min) antes do bloco de contexto/closer, em vez de ir direto ao pitch.
- Produção do vídeo fixo (roteiro, gravação) — artefato a produzir, não decisão de fluxo.

---

## Questões Abertas

1. **Follow-up após vídeo sem resposta (passo 5):** decisão pendente — resolver ainda em 2026-07-01. Opções discutidas: manter padrão v3 (2-3 follow-ups por texto com escassez/dado novo) até Fase 2 estar pronta, vs. outra abordagem.
2. **Passo 2 — pergunta de contexto vs. gap direto:** resolver via teste A/B.
