---
title: "Loops de Retroalimentação"
type: concept
tags: [sistemas, feedback, reforço, balanço]
created: 2026-04-27
updated: 2026-04-27
sources: 1
---

## Definition

Um **loop de retroalimentação** se forma quando mudanças num estoque afetam os fluxos que entram ou saem desse mesmo estoque. Existem dois tipos fundamentais, com comportamentos opostos.

---

## Loop de Balanço (B)

**O que faz:** estabiliza. Busca um estado-alvo e resiste a mudanças que desviem dele.

**Comportamento:** quanto maior o desvio entre estado atual e meta, maior a força corretiva. O sistema "busca" o equilíbrio.

**Exemplos:**
- Termostato: temperatura desce → aquecedor liga → temperatura sobe → aquecedor desliga.
- Churn de clientes: insatisfação aumenta → cancelamentos aumentam → base menor → menos receita → pressão para melhorar produto.
- Feedback do mercado num produto: produto ruim → menos vendas → pressão para corrigir.

**Implicação para a Avalyse:** o sistema de reviews do Google é um loop de balanço — avaliações negativas geram pressão corretiva no negócio. A Avalyse intercepta parte desse loop, mas não pode eliminá-lo sem risco (review gating). [[filtragem-de-avaliacoes]]

---

## Loop de Reforço (R)

**O que faz:** amplifica. Qualquer mudança numa direção é reforçada — crescimento exponencial ou colapso acelerado.

**Comportamento:** mais → ainda mais (ou menos → ainda menos).

**Exemplos:**
- Crescimento viral: mais usuários → mais indicações → mais usuários. [[motores-de-crescimento]]
- Reputação online: mais avaliações positivas → melhor ranking → mais visitas → mais clientes → mais avaliações. [[reputacao-online]]
- "Success to the Successful": primeiro cliente → prova social → segundo cliente mais fácil → mais prova social. [[prova-social]]
- Burnout: trabalho raso crônico → erosão de capacidade → mais trabalho raso necessário para compensar. [[burnout-fundador]]

**Implicação para a Avalyse:** o primeiro cliente é o ponto de ignição do loop de reforço. Sem ele, não há prova social, não há segundo cliente mais fácil, não há crescimento composto. O esforço pré-primeiro-cliente é estruturalmente maior — não é sinal de que o produto não funciona.

---

## Dominância de loop e comportamento do sistema

Sistemas reais têm múltiplos loops de forças variáveis. O comportamento do sistema muda quando a **dominância muda** — quando um loop que era fraco passa a dominar o sistema.

Exemplo clássico: população cresce (loop de reforço domina) até pressionar recursos (loop de balanço ativa e domina) → crescimento para.

Para startups: crescimento rápido (R domina) até churn ou saturação de mercado (B ativa) → platô ou queda. [[framework-3high-3low]]

---

## Delays e oscilação

Quando um loop de balanço opera com delay (informação atrasada ou resposta lenta), o sistema oscila em vez de convergir suavemente para o equilíbrio. Quanto maior o delay, maior a oscilação.

Aplicação direta: se Thiago mede o resultado do outreach apenas ao final do mês, está operando com um delay de semanas — e vai corrigir demais ou de menos. Medir diariamente (taxa de resposta, taxa de demo) reduz o delay e melhora o controle. [[regra-dos-100]]

## Related Concepts

[[pensamento-sistemico]], [[estoques-e-fluxos]], [[arquetipos-de-sistemas]], [[motores-de-crescimento]], [[construir-medir-aprender]], [[regra-dos-100]]

## Sources

[[thinking-in-systems-meadows-howtoes]]
