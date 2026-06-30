---
title: "Análise do Gargalo de Conversão — Outreach Avalyse"
type: analysis
tags: [avalyse, outreach, conversão, gargalo, cold-outreach]
created: 2026-06-24
updated: 2026-06-24
---

> Atualizado via protocolo [[protocolo-semanal]] (keyword: NEW DATA).

---

## Estado atual

Taxa msgs → reunião: **~0.25%** (400 msgs, 1 reunião — amostra pequena).
Benchmark estimado original: 8% msgs→resposta × 35% resposta→demo = ~2.8% implícito.

O funil está quebrando, mas **onde exatamente** ainda é desconhecido por falta de tracking por etapa.

---

## Etapas do funil e hipóteses de quebra

### Etapa 1 — Quebra-gelo → sem resposta
**Sinal:** não há dado segmentado desta etapa.
**Hipóteses:**
- Mensagem parece spam por falta de contexto pessoal
- Horário de envio inadequado
- Número sem histórico (warmup insuficiente) → baixa entrega

### Etapa 2 — Lead Magnet → sem resposta ao diagnóstico
**Sinal:** padrão de "enrolando" identificado no log (jun/2026) — prospects respondem mas não convertem.
**Hipóteses:**
- Diagnóstico desperta curiosidade mas não urgência suficiente para agir
- Prospect vê como spam após receber o diagnóstico numérico
- CTA de "20min de setup" parece fricção alta para quem não conhece a Avalyse
- Frame de "validação" pode reduzir credibilidade em vez de criar reciprocidade

### Etapa 3 — Diagnóstico+Pitch → não agenda reunião
**Sinal:** taxa de meeting muito baixa mesmo entre quem respondeu.
**Hipóteses:**
- O prospect entende o problema mas não percebe urgência para resolver agora
- "Trial 7 dias sem cartão" soa bom demais → gera ceticismo
- Sem prova social própria, o pitch não é crível o suficiente

---

## O que foi testado

| Versão | Mudança | Resultado |
|--------|---------|-----------|
| V1/V2 | Funil em 2 etapas (diagnóstico separado do pitch) | ~300 msgs, 1 lead qualificado |
| V3 | Funil colapsado (diagnóstico + pitch em 1 mensagem) | ~400 msgs, 1 reunião (~0.25%) |

V3 mostrou melhora qualitativa (menos "enrolando" pós-diagnóstico) mas taxa absoluta ainda baixa.

---

## O que ainda não foi testado

- Variante com prova social real (quando disponível)
- Horários diferentes de envio
- Nicho oficina mecânica e clínica veterinária (sugeridos mas não testados)
- Follow-up por cold call após não-resposta no WhatsApp
- Abordagem pelo Instagram DM como canal paralelo

---

## Hipótese principal (2026-06-24)

O gargalo **não está na abertura** (prospects respondem). Está na **conversão resposta → reunião**. A mensagem desperta curiosidade, mas o CTA de trial direto por WhatsApp frio não tem credibilidade suficiente sem prova social própria.

**Teste recomendado:** após fechar o primeiro cliente, substituir o frame de "validação" por case real e medir se a taxa de reunião sobe.

---

## Related

[[entities/avalyse]], [[sources/avalyse-scripts-cold-outreach-v1]], [[analyses/metricas-execucao-avalyse]], [[anti-ban-whatsapp]], [[concepts/outreach]]
