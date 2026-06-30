---
title: "Protocolo de Atualização Semanal — NEW DATA"
type: analysis
tags: [protocolo, métricas, operações, avalyse]
created: 2026-06-24
updated: 2026-06-24
---

## Trigger

Quando o usuário digitar **NEW DATA**, executar imediatamente o protocolo abaixo.

---

## Questionário (enviar tudo de uma vez)

```
Semana de __/__  a __/__ de 2026 — responda tudo que souber, pule o que não tiver:

1. Arquivo CSV com os dados de envio, resposta de prospecção
3. Reuniões agendadas / realizadas / no-show
4. Trials iniciados
5. Clientes pagantes (total acumulado)
6. Incidentes de ban (sim/não — se sim, quantos e tempo de recuperação)
7. Mudança na operação ou produto (nova feature, novo nicho, script alterado, etc.)
8. Atualização do que aconteceu na semana
```

---

## Regra principal de atualização

**Cada dado recebido deve ser refletido em TODAS as páginas onde ele é relevante — não apenas registrado em uma página central.**

Exemplos:
- Mudou algo no Bulker → atualizar `entities/whatsapp-bulker.md`
- Script de outreach alterado → atualizar a source do script correspondente em `sources/`
- Novo nicho testado → atualizar `entities/avalyse.md` (tabela de nichos)
- Ban ocorreu → atualizar `entities/whatsapp-bulker.md` + `analyses/estrategia-anti-ban-whatsapp.md`
- Nova reunião realizada → atualizar `entities/avalyse.md` (Key Facts) + `analyses/metricas-execucao-avalyse.md` + `analyses/gargalo-conversao-outreach.md` (se revelou nova hipótese)

Nunca criar apenas uma entrada no log e considerar feito. O log é o registro histórico — as páginas de entidade e análise são a fonte de verdade atual.

---

## Mapa completo — dado → páginas a atualizar

| Dado recebido | Páginas a atualizar |
|---------------|-------------------|
| Números do funil (msgs, respostas, reuniões, trials, clientes) | `entities/avalyse.md` + `analyses/metricas-execucao-avalyse.md` |
| Incidente de ban / mudança no Bulker | `entities/whatsapp-bulker.md` + `analyses/estrategia-anti-ban-whatsapp.md` |
| Script alterado (outreach, cold call, demo) | Source correspondente em `sources/` + `entities/avalyse.md` se afeta o funil |
| Novo nicho testado ou descartado | `entities/avalyse.md` (tabela de nichos) |
| Reunião realizada — resultado e objeções | `analyses/metricas-execucao-avalyse.md` + `analyses/gargalo-conversao-outreach.md` + `analyses/deadline-primeiro-cliente-2026-07-15.md` |
| Cliente fechado / trial iniciado | `entities/avalyse.md` + `analyses/metricas-execucao-avalyse.md` + `analyses/deadline-primeiro-cliente-2026-07-15.md` |
| Mudança de pricing | `entities/avalyse.md` + source de contexto do produto |
| Mudança no produto / GHL | `entities/avalyse.md` + entidade ou conceito relevante |
| Gargalo identificado | `analyses/gargalo-conversao-outreach.md` |
| Tudo | `wiki/log.md` (prepend, operation `update`) |

---

## Formato da entrada no log

```markdown
## [YYYY-MM-DD] update | Weekly sync — semana DD/MM a DD/MM

- [dado 1 relevante]
- [dado 2 relevante]
- [gargalo ou mudança principal]
```

---

## Regra

Nunca pular a atualização do `log.md`. É o registro histórico da operação.
