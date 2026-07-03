---
title: "NFC Review Card"
type: concept
tags: [produto, reputacao-online, coleta-de-reviews, hardware, lead-magnet, restaurantes]
created: 2026-07-03
updated: 2026-07-03
sources: 1
---

## Definition

Cartão físico com chip NFC (Near Field Communication) programado com a URL de avaliação do Google de um estabelecimento específico. Quando o cliente aproxima o celular do cartão, o browser abre automaticamente a página de avaliação — sem app, sem conta, sem etapas adicionais. Funciona em qualquer smartphone moderno com NFC ativo (padrão em Android desde 2012; iPhone desde o XS/iOS 14 para links externos).

Diferença fundamental em relação ao fluxo WhatsApp da [[Avalyse]]: **não exige que o estabelecimento possua o número de celular do cliente.** O gatilho é físico e voluntário — o cliente toca porque quer, não porque recebeu uma mensagem.

## Evidence & Examples

- Fornecedor chinês identificado pela [[Avalyse]] (2026-07-03) consegue produzir e importar cartões a custo unitário baixo — estimativa em dezenas de centavos a poucos reais por unidade. [[pesquisa-restaurantes-nfc-2026-07-03]]
- Modelo de aquisição testado: entregar 1 cartão gratuitamente ao estabelecimento durante visita presencial → demonstrar o funcionamento na hora → proposta de pacote. [[pesquisa-restaurantes-nfc-2026-07-03]]
- Restaurantes visitados demonstraram interesse — um segmento que até então era inviável para o produto WhatsApp por falta de coleta de dados. [[pesquisa-restaurantes-nfc-2026-07-03]]

## Mecânica técnica

1. Fornecedor grava URL no chip NFC do cartão durante fabricação (ou o chip é reescritável e programado na entrega).
2. URL pode ser: (a) link direto do Google review do estabelecimento; ou (b) URL de redirecionamento intermediária (ex: `avalyse.com/r/[id-cliente]`) — que passa pelo sistema da Avalyse antes de ir ao Google.
3. A opção (b) permite rastrear analytics (número de taps, conversão tap→review) e potencialmente inserir uma página de pré-filtro.

## Counter-evidence & Tensions

- **Sem filtragem de sentimento:** o NFC card não distingue clientes satisfeitos de insatisfeitos. Qualquer pessoa que toque o cartão pode escrever qualquer avaliação. Isso é o oposto do diferencial de [[filtragem-de-avaliacoes]] da Avalyse — mas é eticamente mais correto (evita [[review-gating]]).
- **Sem coleta de dados do cliente:** o estabelecimento não obtém nome, celular ou email da pessoa que avaliou. Perde a possibilidade de follow-up, remarketing ou relacionamento.
- **Dependência de comportamento ativo do cliente:** o cliente precisa querer avaliar e ter NFC ativo. A taxa de conversão é estruturalmente menor que WhatsApp (que é um push ativo para o cliente).
- **Modelo de receita não-recorrente por padrão:** venda de cartões é transação única. Não gera MRR sem uma camada de serviço adicional.

## Related Concepts

[[lead-magnet]], [[reputacao-online]], [[prova-social]], [[google-meu-negocio]], [[filtragem-de-avaliacoes]], [[review-gating]], [[ativo-silencioso]]

## Sources

[[sources/pesquisa-restaurantes-nfc-2026-07-03]]
