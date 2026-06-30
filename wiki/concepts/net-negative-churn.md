---
title: "Net Negative Churn"
type: concept
tags: [saas, métricas, churn, expansion-revenue, walling]
created: 2026-04-15
updated: 2026-04-15
sources: 1
---

## Definition

Estado onde a **expansion revenue** (clientes existentes pagando mais) supera a **receita perdida por churn** (cancelamentos). O resultado é crescimento de MRR mesmo sem adicionar novos clientes.

Definição matemática:

> **Net Churn Rate = Gross Churn Rate − Expansion Revenue Rate**

Se Gross Churn = 3% e Expansion Revenue = 5%, Net Churn = -2% → o negócio ganha 2% de MRR adicional por mês só com clientes existentes.

## Por que é um "SaaS Cheat Code"

- **Crescimento sem aquisição**: O negócio avança mesmo em meses sem novos clientes.
- **Flywheel acelerado**: Quando combinado com aquisição de novos clientes, o crescimento é drasticamente mais rápido.
- **CAC efetivamente menor**: Upsell de cliente existente custa muito menos do que adquirir novo.
- **Resiliência**: Um negócio com net negative churn pode absorver temporadas ruins de aquisição sem decrescer.

## Como alcançar

Dois pré-requisitos simultâneos:
1. **Gross churn baixo** (0-3%): sem isso, a expansion revenue não basta.
2. **Expansion revenue estrutural**: precificação com value metric (uso, seats, subscribers) que sobe automaticamente com o crescimento do cliente.

Walling nota que chegar a net negative churn é raro e exige que ambas as condições estejam bem calibradas.

## Evidence & Examples

- **HitTail** (SEO tool de Walling): 8% churn, 3% expansion revenue → net churn de +5%. Expansion não foi suficiente para compensar. [[saas-playbook-walling-howtoes]]
- **API company** (exemplo anônimo): 2% gross churn, 3% expansion revenue → net churn de -1%. Produto caro e sticky permitiu atingir o estado. [[saas-playbook-walling-howtoes]]
- **TinySeed company** segmento B: -4% net churn no tier de $100/mês. Clientes cresciam e faziam upgrade automaticamente via value metric. [[saas-playbook-walling-howtoes]]

## Counter-evidence & Tensions

- Net negative churn pressupõe que clientes crescem com o tempo — válido para ferramentas B2B onde o cliente escalável (ex.: de 100 para 1.000 subscribers) é o ideal. Em nichos estáticos ou com clientes de tamanho fixo, expansion revenue é difícil de estruturar.
- Walling admite que é "difícil de alcançar" — não é uma estratégia de fase inicial, mas um objetivo de médio-longo prazo.

## Related Concepts

[[framework-3high-3low]], [[bootstrapping-saas]], [[precificacao-premium]], [[motores-de-crescimento]]

## Sources

[[saas-playbook-walling-howtoes]]
