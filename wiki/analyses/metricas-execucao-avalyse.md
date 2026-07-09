---
title: "Dashboard de Métricas — Execução Avalyse"
type: analysis
tags: [avalyse, métricas, funil, execução]
created: 2026-06-24
updated: 2026-07-09
---

> Atualizado via protocolo [[protocolo-semanal]] (keyword: NEW DATA). Última atualização: 2026-07-09.

---

## Funil Acumulado

| Etapa | Volume | Taxa |
|-------|--------|------|
| Mensagens disparadas (acumulado) | ~407 | — |
| Quebra-gelo enviados (período) | 214 | — |
| Quebra-gelo respondidos | 27 | 12,6% (acima do benchmark 8%) |
| Follow-up enviados | 27 | — |
| Follow-up respondidos | 15 | 55,6% |
| Reuniões agendadas | 1 (+ 2 informais na semana 2026-07-09, fora do funil de tracking) | — |
| Convertidos (resposta → próximo passo) | 1 | — |
| Trials iniciados | 1 (Hey Peppers — encerrado sem conversão) | — |
| Clientes pagantes | 0 | — |

**Período da última atualização de dados:** 2026-05-25 a 2026-07-09. Sem novas mensagens disparadas desde 2026-06-24 — número banido.

---

## Performance por campanha (acumulado)

| Campanha | Msgs | Entrega | Leitura | Resposta | Convertidos |
|----------|------|---------|---------|----------|-------------|
| Óticas ABC | 75 | 98,7% | 66,7% | 56,0% | 0 |
| Leads \| Estética \| Curitiba | 157 | 95,5% | 30,6% | 5,7% | 1 |
| Academias SP | 168 | 100,0% | 32,7% | 1,2% | 0 |

**Destaques:** Óticas ABC tem taxa de resposta altíssima (56%) mas 0 convertidos — gargalo está pós-resposta. Academias SP confirma nicho ruim. Estética Curitiba gerou 1 convertido.

---

## Histórico Semanal

| Semana | Msgs | Respostas | Reuniões agendadas | Reuniões realizadas | Trials | Clientes | Ban? |
|--------|------|-----------|-------------------|--------------------|----|---------|------|
| até 2026-06-18 | ~400 | desconhecido | 1 | 0 | 0 | 0 | sim (1x, ~2h) |
| 2026-05-25 a 2026-06-24 | 241 (período) | 27 QB + 15 FU | 1 | desconhecido | 0 | 0 | sim (22/06, duração desconhecida) |
| 2026-06-24 a 2026-07-09 | 0 (banido) | 0 | 2 (informais, fora do funil) | desconhecido | 0 novos — Hey Peppers deu ghost | 0 | sim, mesmo ban de 22/06, ainda ativo (>15 dias) |

---

## Benchmarks de referência (plano original)

Do [[analyses/plano-30-dias-avalyse-encerrado]] — estimativas teóricas, não validadas:

| Etapa | Taxa estimada |
|-------|--------------|
| Msg → resposta | 8% |
| Resposta → demo agendada | 35% |
| Demo → trial | 60% |
| Trial → pagante | 40% |

Taxa real atual (msgs → reunião): **~0.25%** — muito abaixo do estimado. Ver [[analyses/gargalo-conversao-outreach]] para hipóteses.

---

## Infraestrutura de outreach

| Item | Status |
|------|--------|
| WhatsApp Bulker | Produção (fases 0–7 completas) |
| Limite seguro de volume/dia | ~60 msgs/dia (warmup completo) — ban ocorre acima disso |
| Números ativos | desconhecido |
| Listas de leads (Clay) | ativas |

---

## Trials ativos

Nenhum trial ativo no momento (2026-07-09).

| Cliente | Nicho | Início | Duração | Resultado |
|---------|-------|--------|---------|-----------|
| Hey Peppers (Niqui Lang, RS) | Escola | 2026-06-26 | 7 dias | **Encerrado — dono deu ghost.** Não converteu para pagante. |

---

## MRR

| Data | MRR | Clientes | Trials | Meta |
|------|-----|----------|--------|------|
| 2026-06-25 | R$0 | 0 | 1 | R$30k até fim de 2026 |

---

## Notas

- Padrão identificado (jun/2026): prospects respondem ao diagnóstico mas "enrolam" antes de converter — gargalo está no fechamento, não na abertura.
- V3 (funil colapsado) mostrou melhor conversão que V1/V2, mas taxa absoluta ainda baixa.
- Teto de capacidade GHL: 2 clientes simultâneos até MRR ≥ R$1.500.
- **Novo padrão (2026-07-09):** o único trial ativo até então (Hey Peppers) também "enrolou" e sumiu — o gargalo de ghosting agora aparece em duas etapas do funil (pós-diagnóstico e pós-trial), não só na abertura.
- Pivot de produto em andamento: oferta diversificada por nicho (cards NFC para restaurante) e nova estratégia de outbound via vídeo personalizado — ver [[oferta-diversificada-por-nicho]] e [[loom-outreach-personalizado]]. Sem dado de conversão ainda.
