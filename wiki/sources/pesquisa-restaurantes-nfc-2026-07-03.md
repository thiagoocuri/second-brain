---
title: "Pesquisa de Campo — Restaurantes: Gestão de Reputação e NFC Cards"
type: source
tags: [pesquisa-qualitativa, restaurantes, nfc, reputacao-online, avalyse, produto]
created: 2026-07-03
updated: 2026-07-03
raw: "raw/pesquisa-restaurantes-nfc-2026-07-03.md"
---

## Summary

Pesquisa de campo realizada por [[thiago-ccuri]] em 2026-07-03: visitas presenciais a restaurantes para avaliar interesse em serviços de gestão de reputação online. Método: entrevistas informais com donos ou responsáveis no próprio estabelecimento.

Achado central: a maioria dos restaurantes visitados **não precisa** — ou não percebe valor — no serviço de automação de envio de pedidos de avaliação via WhatsApp. A razão estrutural é a mesma já identificada no wiki: restaurantes raramente coletam número de celular dos clientes, eliminando o pré-requisito técnico da Avalyse atual. O modelo de negócio transacional (cliente entra, come, vai embora sem deixar dados) é fundamentalmente incompatível com o fluxo WhatsApp.

Porém, surgiu interesse genuíno em uma solução **diferente**: coleta de avaliação no ponto de contato físico, sem necessidade de dados do cliente. O mecanismo: um cartão físico com NFC (Near Field Communication) que, ao ser aproximado ao celular pelo próprio cliente, abre diretamente a página de avaliação do Google do estabelecimento. Um fornecedor chinês identificado pelo fundador consegue produzir e importar esses cartões a custo baixo.

O modelo de negócio explorado: entregar **1 cartão gratuitamente** (lead magnet presencial) e cobrar pelos demais. Isso reposiciona a aquisição de clientes de outbound digital (WhatsApp Bulker) para outbound físico (visita + produto tangível).

## Key Claims

- A maioria dos restaurantes visitados não coleta número de celular dos clientes — bloqueio estrutural para WhatsApp automation permanece.
- Existe interesse real em "gerar mais avaliações" — o problema de reputação é percebido, mas a solução precisa encaixar no fluxo do restaurante (sem dados do cliente, sem processo novo).
- O cartão NFC resolve o problema de coleta de forma radicalmente mais simples: cliente toca o cartão → celular abre a página de avaliação. Zero fricção, zero dados pessoais necessários.
- Fornecedor chinês identificado consegue fornecer os cartões a custo unitário baixo (estimativa: centavos a poucos reais por unidade).
- Modelo de aquisição proposto: 1 cartão grátis entregue pessoalmente → demonstração do funcionamento → venda de pacotes adicionais.
- Nenhum restaurante expressou interesse no pacote completo de automação WhatsApp + filtro de avaliações.

## Entities

[[avalyse]], [[thiago-ccuri]]

## Concepts

[[reputacao-online]], [[lead-magnet]], [[nfc-review-card]], [[filtragem-de-avaliacoes]], [[prova-social]]

## Contradictions & Tensions

- O interesse em NFC cards **contradiz** a classificação atual de restaurantes como segmento "evitar" em [[entities/avalyse]]. O bloqueio (falta de coleta de celular) se mantém para o produto atual, mas o NFC card contorna esse bloqueio com um produto diferente.
- O NFC card não permite filtragem de sentimento — qualquer cliente (satisfeito ou insatisfeito) pode tocar o cartão e escrever qualquer avaliação. Isso contraria o diferencial atual de [[filtragem-de-avaliacoes]] da Avalyse, mas pode ser mais consistente com as políticas do Google (evitando [[review-gating]]).

## Open Questions

- Qual é o modelo de receita recorrente para o NFC card? Venda de pacotes é one-time — não gera MRR.
- O cartão NFC é um produto autônomo ou um canal de entrada para a venda da automação WhatsApp completa?
- Como configurar o link do cartão (URL de avaliação do Google) por estabelecimento? O processo de customização precisa ser definido.
- Outros segmentos sem coleta de celular se beneficiariam do mesmo produto (varejo, salões de beleza com pagamento em dinheiro)?
- Existe risco legal ou regulatório (LGPD) no uso de NFC para direcionar clientes?
