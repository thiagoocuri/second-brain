# Harmo Funnel Hack — Design Spec
**Data:** 2026-06-12  
**Objetivo:** Reverse-engineering completo do funil do Harmo Reviews para informar pitch, identificar gaps e modelar o funil da Avalyse.

---

## Contexto

A Avalyse é um SaaS de automação de reputação online para negócios locais no Brasil (GHL + WhatsApp API). O Harmo é a principal plataforma BR de gestão de Google Perfil de Empresas e produz a pesquisa Decisão Local — é o concorrente mais próximo e mais estabelecido.

A metodologia base é Funnel Hacking (Russell Brunson, *Dotcom Secrets*, 2014): modelar a estrutura e a psicologia do funil do concorrente, sem copiar conteúdo. Wiki: `wiki/concepts/funnel-hacking.md`.

---

## Objetivos

1. **Melhorar o pitch e a mensagem de vendas** da Avalyse — entender como o Harmo se posiciona e superar o argumento nas calls e no outreach.
2. **Encontrar gaps de mercado** — nichos ignorados, dores não resolvidas, objeções não tratadas pelo Harmo.
3. **Modelar a estrutura do funil** — fluxo completo de atração → conversão → onboarding → retenção como benchmark.
4. **Mapear estratégia de prospecção e marketing** — como o Harmo gera e qualifica leads (canais, mensagens, cadência), quais estratégias de marketing usam ativamente e com que profundidade.

---

## Stack de Ferramentas e Divisão de Trabalho

| Etapa do funil | Ferramenta | Quem executa |
|---|---|---|
| Tráfego orgânico e pago | SEMrush | Usuário |
| Ads ativos (Meta) | Facebook Ads Library + /browse | Assistente + Usuário |
| Conteúdo e posicionamento social | Instagram/Facebook do Harmo | Usuário |
| Website público, pricing, messaging | /browse skill | Assistente |
| Cadastro/trial (se gratuito) | Produto real | Usuário |
| Onboarding + e-mails de ativação | Produto real | Usuário |

---

## Abordagem: Jornada Linear com Template Embutido

Seguir a sequência exata que um prospect do Harmo percorreria, documentando cada etapa com o mesmo conjunto de campos. Ao fim, extrair os insights estratégicos para a Avalyse.

---

## Template de Documentação por Etapa

### Etapa 1 — Descoberta & Tráfego
- Principais keywords orgânicas (volume, dificuldade, posição)
- Keywords pagas ativas (texto dos ads, landing pages de destino, bid estimado)
- Volume de tráfego estimado total e por canal (orgânico, pago, referral, social, direto)
- Canais de mídia paga ativos (Meta, Google, LinkedIn, YouTube, etc.)
- Conteúdo orgânico no social: temas recorrentes, frequência de postagem, engajamento médio, formatos preferidos (vídeo, carrossel, texto)
- Estratégia de conteúdo inferida (educacional, produto, prova social, autoridade)
- Parceiros, co-marketing ou integrações que geram tráfego referral

### Etapa 2 — Website & Messaging
- Headline principal e subheadline
- Proposta de valor declarada
- ICP declarado (quem o Harmo diz atender)
- Gatilhos emocionais e racionais usados
- Tipos e quantidade de prova social (cases, logos, depoimentos, dados)
- CTA principal e secundário
- Objeções tratadas explicitamente na página

### Etapa 3 — Pricing & Oferta
- Planos disponíveis, nomes e preços
- O que está incluído em cada tier
- Modelo de cobrança (mensal/anual, por localização, por volume)
- Garantias ou políticas de cancelamento
- Trial, freemium ou demo disponível
- Ancoragem de preço (como apresentam os planos)

### Etapa 4 — Cadastro & Onboarding *(Usuário executa)*
- Campos pedidos no cadastro (fricção)
- Passos até o primeiro "momento de valor"
- Integrações solicitadas (Google, WhatsApp, etc.)
- Tempo estimado para ativação completa
- Pontos de abandono visíveis

### Etapa 5 — E-mails de Ativação *(Usuário executa)*
- Número de e-mails na sequência de onboarding
- Timing entre cada e-mail
- Linhas de assunto
- Objetivo de cada mensagem (ativar, educar, upsell, reengajar)
- Upsells ou cross-sells embutidos

### Etapa 6 — Estratégia de Prospecção & Marketing *(novo)*
- Como o Harmo prospecta ativamente (outbound, inbound, parcerias, indicações)
- Cadência e canais de outreach identificados (e-mail frio, LinkedIn, WhatsApp, telefone)
- Mensagens de prospecção visíveis (ads de lead gen, formulários, landing pages de captação)
- Estratégia de conteúdo para geração de demanda (blog, YouTube, webinars, relatórios como Decisão Local)
- Posicionamento de autoridade (pesquisas próprias, imprensa, eventos, prêmios)
- Inferências sobre ICP real vs. ICP declarado (quem de fato compra vs. quem o Harmo diz atender)

### Etapa 7 — Gaps & Oportunidades para a Avalyse
- O que o Harmo não cobre (nichos, canais, features)
- Onde a comunicação é fraca ou genérica
- Objeções que o Harmo não trata
- Elementos do funil que a Avalyse pode modelar diretamente
- Elementos que a Avalyse deve fazer diferente
- Ângulos de diferenciação imediata (WhatsApp, onboarding, filtragem, preço, ICP)

---

## Outputs na Wiki

**Source page nova:**  
`wiki/sources/harmo-funnel-hack-2026-06-12.md`  
Formato padrão de source com as 6 seções do template como Key Claims, seção de Contradictions & Tensions (conflitos com a estratégia da Avalyse) e Open Questions.

**Entity page atualizada:**  
`wiki/entities/harmo.md`  
Recebe fatos objetivos confirmados: pricing real, ICP confirmado, canais de tráfego, stack tecnológica visível. Links para a nova source page.

**Analysis page (pós-execução, se necessário):**  
`wiki/analyses/avalyse-vs-harmo-posicionamento-2026-06-12.md`  
Somente se os gaps identificados justificarem um plano de ação separado para a Avalyse.

---

## Sequência de Execução

O relatório é produzido em **7 partes independentes**, uma por etapa do template, para garantir profundidade máxima em cada seção antes de avançar. Nenhuma parte é "rascunho" — cada uma é entregue em nível de publicação final.

| Parte | Etapa | Executor principal | Entregável |
|---|---|---|---|
| 1 | Descoberta & Tráfego | Assistente (/browse) + Usuário (SEMrush, social) | Mapa de tráfego + estratégia de conteúdo |
| 2 | Website & Messaging | Assistente (/browse) | Análise de copy, posicionamento, prova social |
| 3 | Pricing & Oferta | Assistente (/browse) | Mapa de planos + análise de ancoragem |
| 4 | Cadastro & Onboarding | Usuário (trial) | Mapa de fricção + tempo até valor |
| 5 | E-mails de Ativação | Usuário (trial) | Sequência completa anotada |
| 6 | Estratégia de Prospecção & Marketing | Assistente + Usuário | Mapa de outbound/inbound + ICP real |
| 7 | Gaps & Oportunidades | Assistente (síntese) | Lista priorizada de ações para a Avalyse |

**Protocolo por parte:**
- Assistente executa a coleta da parte via /browse ou a partir dos dados entregues pelo usuário
- Assistente apresenta os achados em formato técnico detalhado antes de escrever na wiki
- Usuário valida ou corrige
- Assistente escreve a seção final na source page e só então avança para a próxima parte

---

## Padrão de Qualidade do Relatório

Cada parte deve atender todos os critérios abaixo antes de ser finalizada:

- **Dados reais, não inferências** — toda afirmação deve citar a fonte (URL, screenshot descrito, e-mail recebido). Inferências são permitidas apenas quando explicitamente marcadas como tal.
- **Técnico e específico** — sem generalizações ("o Harmo usa prova social"). O correto: "o Harmo exibe 3 logos de clientes enterprise na hero section + 1 depoimento em vídeo abaixo do pricing."
- **Comparativo com a Avalyse** — cada achado relevante termina com uma nota de implicação direta para a Avalyse (o que fazer igual, diferente ou melhor).
- **Sem redundância entre partes** — cada parte cobre só o seu escopo; insights cross-parte ficam reservados para a Parte 7.

## Critérios de Sucesso

- 7 partes produzidas e validadas individualmente antes de consolidar a source page
- Todas as seções com dados reais citados (zero afirmações sem fonte)
- Pelo menos 5 gaps acionáveis identificados e priorizados para a Avalyse na Parte 7
- Source page publicada em `wiki/sources/harmo-funnel-hack-2026-06-12.md`
- Harmo entity atualizada com fatos confirmados
- Pelo menos 1 elemento do funil do Harmo que a Avalyse pode modelar imediatamente no outreach ou pitch
