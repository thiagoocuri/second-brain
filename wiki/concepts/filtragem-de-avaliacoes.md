---
title: "Filtragem de Avaliações"
type: concept
tags: [reputacao-online, produto, saas, google-reviews]
created: 2026-04-15
updated: 2026-04-18
sources: 2
---

## Definition

Técnica de roteamento que intercepta o feedback do cliente antes de chegar ao Google, separando avaliações positivas (direcionadas ao perfil público) de negativas (direcionadas a canal privado). Protege a nota média e o ranking sem suprimir o feedback real — o dono recebe e pode agir sobre o feedback negativo, mas ele não prejudica a reputação pública.

## Evidence & Examples

Na [[Avalyse]], a implementação funciona via subpágina com 4 emojis:
- 2 emojis positivos → redirecionam ao Google (avaliação pública)
- 2 emojis negativos → redirecionam a formulário interno (só o dono vê)

O cliente final escolhe um emoji sem necessariamente saber que está sendo roteado. [[avalyse-contexto-produto-v1]]

## Counter-evidence & Tensions

- **Review gating é violação explícita das políticas do Google.** O artigo [[how-reviews-affect-google-rankings]] (Reviewly.ai, jan/2026) afirma que "geração ética significa encorajar feedback autêntico — não filtragem seletiva." O sistema de emojis da Avalyse se enquadra tecnicamente na definição de review gating: o cliente negativo é desviado antes de chegar ao Google.
- **Risco de padrão detectável:** nota muito alta com zero reviews negativos em volume alto é um sinal suspeito. O Google pode remover reviews ou penalizar o perfil.
- **Perda de sinal semântico:** o sistema de emojis pode aumentar volume de avaliações mas reduzir o conteúdo textual de cada uma. O Google valoriza texto com keywords (bairro, serviço, resultado) — reviews de emoji puro não contribuem para relevância semântica. [[how-reviews-affect-google-rankings]]
- Eticamente, o consumidor pode entender que sua opinião negativa será publicada quando na prática é capturada internamente.

## Related Concepts

[[reputacao-online]], [[prova-social]], [[google-meu-negocio]], [[review-gating]]

## Sources

[[avalyse-contexto-produto-v1]], [[how-reviews-affect-google-rankings]]
