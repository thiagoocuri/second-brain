---
title: "Review Gating"
type: concept
tags: [reputacao-online, google, risco, filtragem, avalyse]
created: 2026-06-24
updated: 2026-06-24
sources: 2
---

## Definition

Prática de filtrar clientes antes de solicitar avaliação pública — direcionando apenas os satisfeitos para plataformas como o Google, enquanto os insatisfeitos são redirecionados para canais privados. O objetivo é proteger a nota pública do negócio de reviews negativos.

É exatamente o mecanismo central da [[entities/avalyse]]: link → 4 emojis → positivos vão ao Google, negativos vão a formulário interno.

---

## Posição do Google

O Google proíbe explicitamente review gating nas suas políticas de avaliações. Trecho relevante das diretrizes:

> "Não desencoraje nem proíba avaliações negativas, nem solicite avaliações positivas de clientes de forma seletiva."

Isso inclui sistemas que filtram o sentimento antes de encaminhar ao Google — o que é precisamente o que a Avalyse faz.

---

## Risco real para a Avalyse

| Risco | Descrição |
|-------|-----------|
| Remoção de avaliações | Google pode remover reviews coletadas via sistema de filtragem |
| Penalização de ranking | Perfil do cliente pode ser penalizado no Google Maps |
| Suspensão do Perfil Google | Em casos extremos, o Google pode suspender o Perfil do cliente |
| Risco reputacional para a Avalyse | Se identificado, o produto da Avalyse vira o vetor do problema para o cliente |

Na prática, o Google raramente penaliza ativamente — mas o risco existe e é real.

---

## Evidence & Examples

- [[entities/reviewly-ai]] se posiciona explicitamente como anti-review-gating, sugerindo que vê nisso uma vulnerabilidade competitiva da Avalyse. [[sources/how-reviews-affect-google-rankings]]
- A tensão foi registrada em [[avalyse-contexto-produto]] como open question sem resolução.

---

## Como a Avalyse pode se proteger

1. **Reframe do produto:** em vez de "filtrar antes de enviar ao Google", posicionar como "gestão de feedback interno + incentivo a avaliações". O link ainda vai ao Google, mas sem a tela de emojis que filtra explicitamente.
2. **Remover a tela de filtragem:** enviar todos os clientes direto ao Google e usar o formulário interno como canal separado e opcional. Perde o diferencial de proteção mas elimina o risco.
3. **Aceitar o risco conscientemente:** manter o mecanismo atual, monitorar se o Google penaliza algum cliente, e ter um plano de resposta.
4. **Construir argumento jurídico:** a política do Google não tem força de lei — apenas contratual. O risco é de perda do canal Google, não de processo.

Decisão sobre qual caminho tomar cabe ao fundador ([[entities/thiago-ccuri]]). Não foi tomada até 2026-06-24.

---

## Counter-evidence & Tensions

- A [[concepts/filtragem-de-avaliacoes]] é apresentada internamente como o **diferencial #2** do produto. Removê-la muda o produto fundamentalmente.
- Concorrentes como Podium e Birdeye também usam mecanismos similares, mas operam nos EUA onde a aplicação da política do Google é diferente.

---

## Related Concepts

[[concepts/filtragem-de-avaliacoes]], [[concepts/reputacao-online]], [[concepts/seo-local]], [[concepts/prova-social]]

## Sources

[[avalyse-contexto-produto]], [[sources/how-reviews-affect-google-rankings]]
