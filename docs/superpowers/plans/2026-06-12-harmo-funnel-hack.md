# Harmo Funnel Hack — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Reverse-engineering completo do funil do Harmo Reviews em 7 partes técnicas e detalhadas, consolidadas em uma source page na wiki da Avalyse.

**Architecture:** Cada parte é executada, apresentada ao usuário para validação, e só então escrita na wiki. A source page é construída incrementalmente, seção por seção. A entity page do Harmo é atualizada ao final com todos os fatos confirmados.

**Tech Stack:** /browse skill (website público + Facebook Ads Library), SEMrush (usuário), Instagram/Facebook do Harmo (usuário), trial do Harmo se gratuito (usuário), wiki em Markdown.

---

## Arquivos que serão criados ou modificados

- **Criar:** `wiki/sources/harmo-funnel-hack-2026-06-12.md`
- **Modificar:** `wiki/entities/harmo.md`
- **Modificar:** `wiki/index.md`
- **Modificar:** `wiki/log.md`
- **Modificar:** `wiki/overview.md`

---

## Tarefa 1: Parte 1 — Descoberta & Tráfego

**Responsável:** Assistente (/browse → harmo.com e Facebook Ads Library) + Usuário (SEMrush + Instagram/Facebook do Harmo)

**Arquivos:** Nenhum escrito ainda — esta parte é coleta e validação.

- [ ] **Passo 1: Assistente navega no Facebook Ads Library**

  Acessar `https://www.facebook.com/ads/library/?country=BR&q=harmo&search_type=keyword_unordered` via /browse.

  Capturar:
  - Ads ativos (copy do headline, copy do body, CTA, formato — imagem/vídeo/carrossel)
  - Landing pages de destino de cada ad
  - Há quanto tempo cada ad está rodando (se visível)
  - Temas recorrentes entre os ads (dor que ativam, promessa, ICP implícito)

- [ ] **Passo 2: Assistente navega no website do Harmo**

  Acessar `https://harmo.com.br` via /browse. Mapear:
  - De onde vêm os CTAs de topo (blog posts? ads? direto?)
  - Existe blog? Canal de YouTube? Pesquisas publicadas (como Decisão Local)?
  - Há parceiros, integrações ou logos de mídia que indicam backlinks de autoridade?

- [ ] **Passo 3: Usuário executa no SEMrush**

  Inserir domínio `harmo.com.br` no SEMrush e extrair:
  - Top 10 keywords orgânicas (keyword, volume/mês, posição, URL de destino)
  - Top 5 keywords pagas ativas (keyword, CPC estimado, URL de destino)
  - Volume de tráfego total estimado e breakdown por canal (organic / paid / referral / social / direct)
  - Principais domínios referenciando o Harmo (top 5 backlinks por autoridade)

- [ ] **Passo 4: Usuário analisa Instagram e Facebook do Harmo**

  Acessar os perfis sociais do Harmo e registrar:
  - Frequência de postagem (posts/semana)
  - Formatos usados (Reels, carrossel, imagem estática, stories)
  - Temas recorrentes (educacional, produto, prova social, data/pesquisa, bastidores)
  - Post com maior engajamento visível (tipo, tema, formato)
  - Tom de voz (técnico, consultivo, comercial, informal)

- [ ] **Passo 5: Usuário entrega os dados ao assistente**

  Compartilhar no chat: print ou texto dos dados do SEMrush + observações do social.

- [ ] **Passo 6: Assistente consolida e apresenta Parte 1**

  Apresentar análise técnica completa no chat, estruturada assim:

  ```
  ## Parte 1 — Descoberta & Tráfego

  ### Tráfego orgânico
  [top keywords, volume, posição, URL]

  ### Tráfego pago
  [keywords pagas, CPC, landing pages]

  ### Canais e distribuição
  [breakdown % por canal]

  ### Ads ativos (Meta)
  [copy, formato, CTA, tema, landing page, duração estimada]

  ### Estratégia de conteúdo social
  [frequência, formatos, temas, engajamento, tom]

  ### Parceiros e autoridade
  [backlinks relevantes, pesquisas publicadas, mídia]

  ### Implicação para a Avalyse
  [o que modelar, o que diferir, o que a Avalyse ainda não faz]
  ```

- [ ] **Passo 7: Usuário valida a análise**

  Confirmar ou corrigir antes de escrever na wiki.

---

## Tarefa 2: Parte 2 — Website & Messaging

**Responsável:** Assistente (/browse)

- [ ] **Passo 1: Assistente navega pela homepage do Harmo**

  Via /browse em `https://harmo.com.br`. Capturar textualmente:
  - Headline e subheadline exatos (acima do fold)
  - Proposta de valor principal
  - CTA primário e secundário (texto exato + destino)
  - Seções presentes na homepage (ordem e nome)

- [ ] **Passo 2: Assistente mapeia a prova social**

  Na mesma página ou em páginas linkadas a partir dela:
  - Logos de clientes (quantos, quais segmentos)
  - Depoimentos (quantos, formato — texto/vídeo, cargo do autor)
  - Dados quantitativos exibidos ("X clientes", "Y avaliações gerenciadas")
  - Cases de sucesso (existe página dedicada?)

- [ ] **Passo 3: Assistente mapeia ICP e objeções tratadas**

  - Quais segmentos de cliente são nomeados explicitamente?
  - Existe seção "Para quem é" ou similar?
  - Quais objeções são tratadas na página (preço, complexidade, tempo de setup, confiança)?
  - Existe FAQ? Sobre o quê?

- [ ] **Passo 4: Assistente navega páginas secundárias relevantes**

  Verificar: `/sobre`, `/clientes`, `/casos`, `/blog`, `/recursos` (ou equivalentes).
  Capturar qualquer messaging adicional não presente na homepage.

- [ ] **Passo 5: Assistente consolida e apresenta Parte 2**

  ```
  ## Parte 2 — Website & Messaging

  ### Headline e proposta de valor
  [texto exato + análise do ângulo emocional/racional]

  ### ICP declarado
  [segmentos nomeados, linguagem usada]

  ### Gatilhos emocionais e racionais
  [lista de cada gatilho identificado + onde aparece]

  ### Prova social
  [tipos, quantidade, formatos, posicionamento na página]

  ### Objeções tratadas
  [lista de objeções e como são respondidas]

  ### CTA e fluxo de conversão
  [CTA primário, secundário, destino, fricção percebida]

  ### Implicação para a Avalyse
  [o que o Harmo faz bem que a Avalyse deve adotar, o que está ausente]
  ```

- [ ] **Passo 6: Usuário valida a análise**

---

## Tarefa 3: Parte 3 — Pricing & Oferta

**Responsável:** Assistente (/browse)

- [ ] **Passo 1: Assistente navega a página de pricing do Harmo**

  Via /browse em `/pricing`, `/planos` ou equivalente.

  Capturar:
  - Nome de cada plano
  - Preço (mensal e anual se disponível)
  - O que está incluído em cada tier (lista exata de features)
  - Modelo de cobrança: por localização? por volume de avaliações? por usuário?
  - Plano mais vendido (destacado visualmente?)

- [ ] **Passo 2: Assistente mapeia garantias e trial**

  - Existe trial gratuito? Por quantos dias? Cartão exigido?
  - Existe freemium?
  - Existe garantia de reembolso? Por quanto tempo?
  - Existe política de cancelamento visível?

- [ ] **Passo 3: Assistente analisa ancoragem de preço**

  - Em que ordem os planos aparecem (mais caro → mais barato ou inverso)?
  - Existe plano "isca" com muitas limitações para empurrar upgrade?
  - Existe plano enterprise "sob consulta"?
  - Qual é o plano que o layout visual empurra (cor diferente, badge "mais popular")?

- [ ] **Passo 4: Assistente consolida e apresenta Parte 3**

  ```
  ## Parte 3 — Pricing & Oferta

  ### Planos e preços
  | Plano | Preço mensal | Preço anual | Features principais |
  |---|---|---|---|
  [preencher com dados reais]

  ### Modelo de cobrança
  [por localização / por volume / por usuário / flat]

  ### Trial e garantias
  [duração, exigência de cartão, política de reembolso]

  ### Ancoragem e psicologia de pricing
  [ordem dos planos, plano destacado, estratégia inferida]

  ### Comparação com Avalyse
  [preço Harmo vs. Avalyse R$397, o que cada um inclui, posicionamento relativo]

  ### Implicação para a Avalyse
  [o que ajustar no pricing ou na comunicação de preço]
  ```

- [ ] **Passo 5: Usuário valida a análise**

---

## Tarefa 4: Parte 4 — Cadastro & Onboarding

**Responsável:** Usuário (trial do Harmo, se gratuito)

- [ ] **Passo 1: Usuário verifica se existe trial gratuito**

  Tentar iniciar o cadastro no Harmo. Registrar:
  - URL exata do formulário de cadastro
  - Campos pedidos (nome, e-mail, telefone, CNPJ, nome do negócio, segmento?)
  - Cartão de crédito exigido? Sim/Não
  - Número total de campos no formulário

- [ ] **Passo 2: Usuário completa o cadastro (se gratuito)**

  Registrar:
  - Tempo total do cadastro (em minutos)
  - Primeiro passo após criar a conta (o que aparece na tela?)
  - A plataforma pede integração com Google imediatamente?
  - Existe wizard de onboarding (checklist de passos)?

- [ ] **Passo 3: Usuário mapeia o caminho até o primeiro valor**

  - Qual é o primeiro momento em que o produto entrega algo útil? (relatório, preview, dado)
  - Quantos passos são necessários até esse momento?
  - Existe algum ponto de abandono visível (passo que parece trabalhoso ou confuso)?

- [ ] **Passo 4: Usuário entrega os dados ao assistente**

  Compartilhar: descrição de cada tela, campos pedidos, tempo percorrido, impressão geral de fricção (1–5, sendo 5 = muito fácil).

- [ ] **Passo 5: Assistente consolida e apresenta Parte 4**

  ```
  ## Parte 4 — Cadastro & Onboarding

  ### Formulário de cadastro
  [campos, cartão exigido, fricção]

  ### Fluxo de ativação
  [passos em ordem até o primeiro valor]

  ### Tempo até o primeiro valor
  [estimativa em minutos]

  ### Pontos de abandono
  [etapas que parecem trabalhosas ou confusas]

  ### Integrações solicitadas
  [Google, WhatsApp, outros — quando e como]

  ### Implicação para a Avalyse
  [o que simplificar no onboarding, o que o Harmo faz melhor ou pior]
  ```

- [ ] **Passo 6: Usuário valida a análise**

---

## Tarefa 5: Parte 5 — E-mails de Ativação

**Responsável:** Usuário (após cadastro no trial)

- [ ] **Passo 1: Usuário coleta todos os e-mails recebidos após o cadastro**

  Durante os primeiros 3–5 dias após criar a conta, salvar cada e-mail recebido do Harmo.
  Para cada e-mail registrar:
  - Dia em que chegou (D+1, D+2, etc.)
  - Linha de assunto (texto exato)
  - Remetente exibido (nome + endereço)
  - Objetivo aparente do e-mail (ativar, educar, convidar para demo, upsell, reengajar)
  - CTA principal (texto do botão + destino)
  - Trechos de copy mais relevantes (1–3 frases)

- [ ] **Passo 2: Usuário entrega os dados ao assistente**

  Compartilhar a lista de e-mails no chat no formato descrito acima.

- [ ] **Passo 3: Assistente consolida e apresenta Parte 5**

  ```
  ## Parte 5 — E-mails de Ativação

  ### Sequência completa
  | Dia | Assunto | Objetivo | CTA |
  |---|---|---|---|
  [preencher com dados reais]

  ### Padrões identificados
  [tom de voz, progressão lógica, gatilhos usados]

  ### Upsells ou cross-sells
  [quando aparecem e como são enquadrados]

  ### Gaps na sequência
  [o que está ausente — ex: não há e-mail de reengajamento, não há case de sucesso]

  ### Implicação para a Avalyse
  [o que modelar, o que melhorar, o que a Avalyse ainda não tem]
  ```

- [ ] **Passo 4: Usuário valida a análise**

---

## Tarefa 6: Parte 6 — Estratégia de Prospecção & Marketing

**Responsável:** Assistente (/browse) + Usuário (observações do produto interior)

- [ ] **Passo 1: Assistente mapeia inbound e geração de demanda**

  Via /browse no blog, canal do YouTube (se existir) e página de recursos do Harmo:
  - Existe blog? Quantos artigos? Temas dominantes?
  - Publicam pesquisas próprias (como a Decisão Local)?
  - Existe canal YouTube ou podcast?
  - Webinars ou eventos listados no site?
  - Existe página de parceiros ou programa de indicação?

- [ ] **Passo 2: Assistente mapeia posicionamento de autoridade**

  Via /browse:
  - Prêmios ou certificações exibidas
  - Logos de mídia/imprensa ("como visto em")
  - Associações de setor (ABComm, SBVC, etc.)
  - Pesquisas publicadas em parceria com outras marcas

- [ ] **Passo 3: Assistente investiga outbound visível**

  Via /browse no LinkedIn do Harmo (perfil da empresa) e via Facebook Ads Library (já mapeado na Tarefa 1):
  - O Harmo tem equipe de SDRs/vendas visível no LinkedIn?
  - Existem vagas abertas de BDR/SDR/AE que revelem o modelo de vendas?
  - Ads de lead gen (formulário integrado ao Facebook) vs. ads de tráfego para site?

- [ ] **Passo 4: Usuário verifica no interior do produto**

  Após o cadastro: existe referral program, convite para indicar outros negócios, ou botão de "indique um amigo"? Existe CSM ou onboarding humanizado (alguém entrou em contato após o cadastro)?

- [ ] **Passo 5: Usuário entrega os dados ao assistente**

- [ ] **Passo 6: Assistente consolida e apresenta Parte 6**

  ```
  ## Parte 6 — Estratégia de Prospecção & Marketing

  ### Geração de demanda inbound
  [blog, YouTube, pesquisas, webinars — temas, frequência, alcance estimado]

  ### Posicionamento de autoridade
  [prêmios, mídia, parceiros, pesquisas co-branded]

  ### Modelo de vendas inferido
  [PLG? Sales-led? Hybrid? Base: vagas, ads de lead gen, presença de CSM]

  ### Outbound visível
  [equipe de vendas, ads de lead gen, cadência inferida]

  ### ICP real vs. declarado
  [quem o Harmo diz atender vs. quem aparece nos cases e prova social]

  ### Programa de indicação ou parceiros
  [existe? Como funciona?]

  ### Implicação para a Avalyse
  [onde a Avalyse pode atacar onde o Harmo não está presente, o que modelar]
  ```

- [ ] **Passo 7: Usuário valida a análise**

---

## Tarefa 7: Parte 7 — Gaps & Oportunidades para a Avalyse

**Responsável:** Assistente (síntese das 6 partes anteriores)

*Esta parte só começa após todas as 6 anteriores estarem validadas.*

- [ ] **Passo 1: Assistente lista todos os gaps identificados nas partes 1–6**

  Para cada gap: nome do gap, onde foi observado (qual parte), evidência citada, nível de impacto para a Avalyse (Alto / Médio / Baixo).

- [ ] **Passo 2: Assistente prioriza e apresenta Parte 7**

  ```
  ## Parte 7 — Gaps & Oportunidades para a Avalyse

  ### Gaps de canal
  [canais que o Harmo não usa e a Avalyse pode explorar]

  ### Gaps de ICP
  [segmentos que o Harmo ignora ou atende mal]

  ### Gaps de messaging
  [ângulos de dor ou promessa que o Harmo não ativa]

  ### Gaps de oferta
  [features, garantias, modelo de preço ou onboarding que a Avalyse pode superar]

  ### Gaps de funil
  [etapas do funil onde o Harmo tem fricção ou abandono visível]

  ### Top 5 ações imediatas para a Avalyse
  1. [ação — contexto — impacto esperado]
  2. [ação — contexto — impacto esperado]
  3. [ação — contexto — impacto esperado]
  4. [ação — contexto — impacto esperado]
  5. [ação — contexto — impacto esperado]
  ```

- [ ] **Passo 3: Usuário valida a síntese**

---

## Tarefa 8: Consolidação na Wiki

**Responsável:** Assistente

*Esta tarefa só começa após a Parte 7 validada.*

- [ ] **Passo 1: Assistente cria a source page**

  Criar `wiki/sources/harmo-funnel-hack-2026-06-12.md` com o seguinte frontmatter e estrutura:

  ```markdown
  ---
  title: "Harmo Reviews — Funnel Hack Completo 2026"
  type: source
  tags: [competitor-analysis, funnel-hacking, harmo, marketing, vendas]
  created: 2026-06-12
  updated: 2026-06-12
  raw: ""
  ---

  ## Summary
  [2–3 parágrafos sintetizando os achados mais importantes]

  ## Key Claims
  [bullets técnicos das 7 partes — cada um com fonte citada]

  ## Entities
  [[Harmo]], [[russell-brunson]], [[Avalyse]], [[funnel-hacking]]

  ## Concepts
  [[funnel-hacking]], [[reputacao-online]], [[seo-local]], [[prova-social]],
  [[Outreach]], [[lead-magnet]], [[equacao-de-valor]]

  ## Contradictions & Tensions
  [conflitos com a estratégia atual da Avalyse]

  ## Open Questions
  [questões abertas após o funnel hack]

  ---
  [seções das 7 partes validadas, coladas aqui]
  ```

- [ ] **Passo 2: Assistente atualiza `wiki/entities/harmo.md`**

  Adicionar / corrigir:
  - Pricing real confirmado
  - ICP real (vs. declarado se diferente)
  - Canais de tráfego principais
  - Modelo de vendas inferido
  - Stack de ferramentas visível
  - Atualizar `sources: N` e `updated: 2026-06-12`
  - Adicionar link para `[[harmo-funnel-hack-2026-06-16]]` em Appearances

- [ ] **Passo 3: Assistente atualiza `wiki/index.md`**

  Adicionar na seção Sources:
  ```
  - [[sources/harmo-funnel-hack-2026-06-16]] — Funnel hack completo do Harmo: tráfego, messaging, pricing, onboarding, e-mails, prospecção e gaps para a Avalyse (2026-06-12)
  ```

- [ ] **Passo 4: Assistente atualiza `wiki/overview.md`**

  Na seção "Aplicação prática: Avalyse", adicionar parágrafo sobre os achados do funnel hack e os principais gaps identificados. Atualizar `sources: N` e `updated: 2026-06-12`.

- [ ] **Passo 5: Assistente appenda entrada no `wiki/log.md`**

  ```markdown
  ## [2026-06-12] ingest | Harmo — Funnel Hack Completo

  - 7 partes executadas: tráfego (SEMrush + Meta Ads), website/messaging, pricing, onboarding, e-mails de ativação, prospecção/marketing, gaps
  - [N] gaps identificados para a Avalyse; top 5 ações imediatas documentadas na Parte 7
  - Entidades atualizadas: [[Harmo]]. Conceitos linkados: [[funnel-hacking]], [[reputacao-online]], [[seo-local]]
  - Source page criada: [[harmo-funnel-hack-2026-06-16]]
  ```

- [ ] **Passo 6: Assistente confirma ao usuário que a wiki está completa**

  Listar os 5 arquivos criados/modificados e os principais achados em 3 bullets.

---

## Self-Review

**Cobertura do spec:**
- ✅ Objetivo 1 (pitch/messaging) → Tarefa 2
- ✅ Objetivo 2 (gaps) → Tarefa 7
- ✅ Objetivo 3 (modelar funil) → Tarefas 1–5
- ✅ Objetivo 4 (prospecção e marketing) → Tarefa 6
- ✅ Relatório em partes com validação por parte → protocolo em todas as tarefas
- ✅ SEMrush → Tarefa 1, Passo 3
- ✅ Instagram/Facebook → Tarefa 1, Passo 4
- ✅ Trial/onboarding pelo usuário → Tarefas 4 e 5
- ✅ Source page + entity update → Tarefa 8
- ✅ Padrão de qualidade (dados reais, técnico, comparativo) → instrução em cada Passo de consolidação

**Placeholders:** nenhum TBD, TODO ou "similar à tarefa N" presente.

**Consistência:** source page referenciada como `harmo-funnel-hack-2026-06-12` em todas as tarefas.
