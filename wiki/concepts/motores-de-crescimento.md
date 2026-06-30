---
title: "Motores de Crescimento"
type: concept
tags: [lean-startup, crescimento, negócios]
created: 2026-04-14
updated: 2026-04-14
sources: 1
---

## Definition

Os mecanismos pelos quais uma startup cresce de forma sustentável. [[eric-ries]] identifica três motores distintos — cada um com sua lógica própria de métricas e otimização. Identificar qual motor move seu negócio é fundamental para saber o que medir e onde investir.

## Os 3 Motores

| Motor | Mecanismo | Métrica-chave |
|---|---|---|
| **Recorrente** | Retenção de clientes gera receita recorrente | Taxa de churn |
| **Viral** | Clientes fazem o marketing — produto se espalha por uso | Coeficiente viral (K) |
| **Pago** | Investimento em aquisição de clientes | LTV vs. CAC |

- **Recorrente:** crescimento vem de reter quem já é cliente. Churn baixo é mais importante do que aquisição.
- **Viral:** cada usuário traz outros usuários. O coeficiente viral (quantos novos usuários cada usuário gera) deve ser > 1 para crescimento exponencial.
- **Pago:** crescimento depende de gastar dinheiro para adquirir clientes. Sustentável apenas se LTV > CAC.

## Evidence & Examples

- Facebook no início usava motor viral puro — sem custo de aquisição, crescimento por atração. [[o-que-e-lean-startup-eric-ries]]
- Manter o motor funcionando exige boa estrutura organizacional — não é automático. [[o-que-e-lean-startup-eric-ries]]
- Os motores determinam o [[product-market-fit]]: se nenhum motor está funcionando, o fit ainda não foi alcançado.

## Counter-evidence & Tensions

- Na prática, empresas usam múltiplos motores simultaneamente — a teoria simplifica para clareza de foco, mas o mundo real é híbrido.
- O motor viral depende de comportamento de usuário imprevisível; difícil de engenheirar diretamente.

## Perspectiva de Sistemas

[[donella-meadows]] fornece a estrutura subjacente dos motores de crescimento: cada motor é um **loop de reforço**. O motor viral é um loop R clássico (mais usuários → mais indicações → mais usuários). O motor recorrente é sustentado por um loop de balanço (churn baixo estabiliza a base). O motor pago só funciona se o loop de reforço (LTV > CAC → reinvestimento → mais clientes → mais LTV) dominar o loop de balanço (CAC crescente com escala). [[loops-retroalimentacao]]

Isso explica por que "nenhum motor funcionando" = PMF não atingido: sem loop de reforço dominante, o sistema não tem momentum.

## Related Concepts

[[lean-startup]], [[Pivotar]], [[aprendizagem-validada]], [[contabilidade-de-inovacao]], [[loops-retroalimentacao]], [[pensamento-sistemico]]

## Sources

[[o-que-e-lean-startup-eric-ries]], [[thinking-in-systems-meadows-howtoes]]
