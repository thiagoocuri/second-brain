---
title: "Avalyse — Contexto de Produto, Mercado e Operações v1"
type: source
tags: [saas, produto, mercado, pricing, vendas, avalyse]
created: 2026-04-15
updated: 2026-04-15
raw: "raw/avalyse-contexto-produto-v1.md"
---

## Summary

Documento de contexto operacional da [[Avalyse]] coletado diretamente do fundador. Cobre a arquitetura técnica (GHL + WhatsApp API oficial), o fluxo de setup por cliente, o sistema de filtragem de avaliações como diferencial central, o mapa competitivo (Harmo, Podium, Birdeye, Nice Job, Review Harvest), o funil de vendas atual, pricing e objetivos de 3 meses.

O produto está construído sobre GoHighLevel — stack que resolve o problema rapidamente mas cria dependência e limitações de integração com CRMs externos. O objetivo declarado é migrar para plataforma própria após a primeira validação.

## Key Claims

- O diferencial técnico central é o **sistema de filtragem de avaliações**: link → subpágina com 4 emojis → positivos vão ao Google, negativos vão a formulário privado. Filtra ruído antes de atingir a reputação pública.
- Canal WhatsApp (via API oficial) é o principal diferencial competitivo frente a concorrentes que usam email/SMS — taxa de abertura estruturalmente maior no Brasil.
- Setup completo acontece na própria reunião de fechamento (~20min) — onboarding imediato elimina fricção pós-venda.
- O único gargalo manual é o diagnóstico pré-venda, feito via MapRanking. Todo o pós-setup é automatizado.
- Objeção mais comum na prospecção: "o cliente vê a mensagem e ignora" — problema de abertura/atenção, não de produto.
- Pricing estruturado por número de localizações: Solo R$397/mês (1 localização) · Multi sob consulta (2+). Anual com 2 meses grátis (~R$331/mês efetivo). Modelo anterior (por volume de avaliações) descartado por gerar faturamento variável e confusão no cliente.
- Meta de 3 meses: 1° cliente pagante + início do desenvolvimento da plataforma própria.

## Entities

[[Avalyse]], [[GoHighLevel]], [[Harmo]]

## Concepts

[[reputacao-online]], [[filtragem-de-avaliacoes]], [[google-meu-negocio]], [[bootstrapping-saas]], [[stair-step-method]]

## Contradictions & Tensions

- A prova social atual é baseada em "método similar" — não em clientes próprios da Avalyse. Isso fragiliza o argumento em negociações com prospects mais céticos. Precisa ser substituída por prova própria assim que o 1° cliente tiver resultado.
- Pricing baseado em comparação com concorrentes internacionais (Podium, Birdeye), que operam em mercados com poder de compra muito maior que o BR. O piso de R$397 pode estar descalibrado para o ICP local — confirmar via conversas de vendas.
- A dependência do GHL é um risco de moat: as automações pertencem à plataforma, não à Avalyse. Migração para código próprio é o movimento correto, mas aumenta a complexidade do roadmap.

## Open Questions

- Qual é a taxa de no-show ou "ignora" na prospecção? O gargalo está na abertura da 1ª mensagem ou na resposta ao diagnóstico?
- Como a [[filtragem-de-avaliacoes]] (emojis) se comporta juridicamente? Há risco de violação das políticas do Google de filtragem de reviews?
- O MapRanking tem API ou o diagnóstico não tem caminho de automação no curto prazo?
- Qual é o CAC atual (tempo do fundador por cliente fechado)?
- O onboarding de 20min funciona para todos os segmentos do ICP ou alguns (ex: clínicas com CRM próprio) são mais complexos?
