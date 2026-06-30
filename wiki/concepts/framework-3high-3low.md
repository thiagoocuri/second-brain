---
title: "Framework 3 High/3 Low"
type: concept
tags: [saas, métricas, kpi, churn, pricing, walling]
created: 2026-04-15
updated: 2026-04-15
sources: 1
---

## Definition

Framework de [[rob-walling]] para simplificar o monitoramento de métricas SaaS. Parte das duas "North Star Metrics" (MRR e taxa de crescimento MoM) e adiciona seis KPIs complementares divididos em três que devem ficar **baixos** e três que devem ficar **altos**.

**North Star (lagging indicators — revisar semanalmente):**
- **MRR** (Monthly Recurring Revenue): progresso absoluto
- **MoM Growth Rate**: velocidade do progresso

---

### LOW: Métricas para reduzir

**1. CAC (Custo de Aquisição de Cliente)**

> Todos os custos de aquisição / número de clientes adquiridos no período

- Benchmarks bootstrapped: payback period de **2-6 meses** (VC aceita até 12-18 meses).
- Para esforços orgânicos, valorize o tempo do fundador (ex.: $150/hora) para estimar o "verdadeiro CAC".
- CAC <= 1/3 LTV é regra VC — bootstrappers precisam de retorno mais rápido.

**2. Sales Effort**

> Comprimento do ciclo de venda e número de touchpoints até fechar

- Rastrear: dias médios do primeiro demo ao fechamento; número de ligações para fechar.
- Maneiras de reduzir: self-serve sign-up + onboarding, one-call close, automação de qualificação.
- Referência: $50k ACV justifica ciclo de 3-4 meses; $5k ACV não.

**3. Churn (Revenue Churn)**

> MRR cancelado no mês / MRR inicial do mês

Benchmarks B2B SaaS:
| Churn mensal | Avaliação |
|---|---|
| >10% | Catastrófico |
| 8-10% | Ruim |
| 6-7% | Meh |
| 4-5% | Ok |
| 2-3% | Bom |
| <2% | Excelente |

**Fórmula do platô**: `Platô MRR = Novo MRR / Taxa de Churn`
- Exemplo: $5.000 novo MRR / 10% churn = platô em $50.000 MRR
- Calcular cedo e repetir frequentemente — plateaus são "brutais e difíceis de desfazer."

Segmentar churn por: tier de preço, canal de marketing, coorte (tempo). Churn agregado esconde padrões críticos.

---

### HIGH: Métricas para aumentar

**4. ACV (Annual Contract Value)**

> Quanto um cliente paga em 12 meses

- Walling prefere ACV a LTV para bootstrappers: LTV (ARPA/churn) pode ser alto mas demorar anos para se realizar.
- Para aumentar: vender para empresas maiores, aumentar preços, expansion revenue.

**5. Expansion Revenue**

> Clientes pagando mais conforme extraem mais valor

- Via value metric (uso, seats, subscribers) ou feature gating.
- "SaaS Cheat Code": quando alto o suficiente, leva a [[net-negative-churn]].
- Upsell de cliente existente é muito mais barato que adquirir novo.

**6. Referrals**

> Novos clientes indicados por existentes

- Medir: perguntar no sign-up como o cliente soube da empresa.
- Email automatizado (60-90 dias): "muito do nosso negócio vem de indicações — se você está gostando, pode recomendar?"
- Alta taxa de referrals = flywheel de virality girando.

## Evidence & Examples

- TinySeed company: $30/mês (Segmento A) com 11% net churn, $100/mês (Segmento B) com -4% net churn. 80% da receita vinha do Segmento B → decisão de descontinuar Segmento A. Impossível ver sem segmentar. [[saas-playbook-walling-howtoes]]
- AgentMethods (Aaron Kassover): descobriu que LTV de leads PPC era muito menor que a média — interrompeu PPC para esse segmento, economizando dinheiro. Só possível via churn por canal. [[saas-playbook-walling-howtoes]]
- Gymdesk: aumento de preço de >50% após 6 anos de underpricing. Grandfathered clientes antigos por meses depois moveu para plano com desconto. Resultado: apenas alguns de 600+ clientes saíram, MRR aumentou 25%, crescimento 70%. [[saas-playbook-walling-howtoes]]

## Related Concepts

[[net-negative-churn]], [[bootstrapping-saas]], [[precificacao-premium]], [[product-market-fit]], [[equacao-de-valor]]

## Sources

[[saas-playbook-walling-howtoes]]
