---
title: Avalyse
type: entity
tags:
  - product
  - saas
  - reputacao-online
  - b2b-local
  - avalyse
created: 2026-04-15
updated: 2026-06-27
sources: 8
---

## Overview

SaaS de automação de reputação online para prestadores de serviço locais, fundado por [[thiago-ccuri]]. **Reposicionamento (2026-06-27):** a Avalyse não é gestão de reputação — é ativação do [[ativo-silencioso]]: os clientes satisfeitos que o negócio já tem e não usa. Cada review coletado alimenta três frentes simultaneamente: Google Maps (ranking orgânico), Instagram (conteúdo de prova social), e redução de dependência de tráfego pago. Automatiza o fluxo completo de coleta e filtragem de avaliações no Google Maps via WhatsApp, sem exigir mudança na rotina do cliente. Estágio atual (2026-06-24): validação — 0 clientes pagantes, ~400 msgs disparadas, 1 reunião agendada (primeira demo real). Operação solo, fundador de 17 anos estudando em paralelo.

## Como funciona

**Fluxo pós-atendimento (automatizado):**
1. Cliente final recebe mensagem WhatsApp personalizada
2. Clica no link → cai em subpágina com 4 emojis
3. Emojis positivos → redireciona ao Google (avaliação pública)
4. Emojis negativos → redireciona a formulário interno (só o dono vê)
5. Avaliação recebida → respondida automaticamente
6. Avaliação compartilhada nos Stories do Instagram

**Setup por cliente (manual, feito em reunião de ~20min):**
- Criar subconta no GoHighLevel
- Integrar WhatsApp, Instagram e Google Meu Negócio do cliente
- Integrar CRM nativo do cliente via API (quando disponível) — ver abaixo

**Entrada de contatos pós-atendimento (dois modos):**
- **Com API:** CRM do cliente integrado via GHL API → contato criado automaticamente ao fim do atendimento → workflow dispara em tempo real
- **Sem API:** Funcionário do cliente acessa página dedicada da Avalyse (externa ao GHL) → preenche nome + celular → chamada à GHL API cria o contato na subconta correta → workflow dispara. Cada cliente tem sua própria rota/credencial isolada. **Formulário implementado (jun/2026).**

## Key Facts

- **Tech stack:** GoHighLevel (GHL) + WhatsApp API oficial. [[avalyse-contexto-produto-v1]]
- **Diferencial #1:** Canal WhatsApp — taxa de abertura estruturalmente maior que email/SMS no Brasil. [[avalyse-contexto-produto-v1]]
- **Diferencial #2:** Sistema de filtragem de avaliações (emojis) — filtra negativos antes de chegarem ao Google. [[avalyse-contexto-produto-v1]]
- **Diferencial #3:** Onboarding completo na própria reunião de fechamento (~20min). [[avalyse-contexto-produto-v1]]
- **ICP / Sweet Spot (2026-06-27):** negócio B2C local com Maps, 30–500 reviews, nota 3.8–4.7★, 5+ funcionários, faturamento R$16k–40k/mês, mercado competitivo. Persona: dono ou sócio-gestor que decide sozinho, já tem experiência com marketing digital, considera tempo precioso. Dois tracks de entrada: Track 1 (tráfego pago, via Meta Ads Library) e Track 2 (reviews negativos, via Maps). Ver [[tracks-prospecao]] e [[perfil-de-cliente-ideal]]. [[avalyse-funil-segmentacao-gatilhos-2026-06-27]]
- **Filtro obrigatório de qualificação:** o negócio precisa coletar no mínimo o número de celular dos clientes. Sem isso, é impossível enviar a mensagem WhatsApp pós-atendimento — o produto não funciona. É a primeira pergunta a fazer antes de qualquer demo.
- **Pricing (2026-05-09):** Solo R$397/mês (1 localização) · Multi sob consulta (2+ localizações). Pagamento anual: 2 meses grátis (equivalente a ~R$331/mês). [[avalyse-contexto-produto-v1]]
- **Canal de aquisição:** Cold outreach WhatsApp com diagnóstico gratuito de ranking como isca ([[MapRanking]]), operacionalizado via [[whatsapp-bulker]]. Listas de leads construídas via [[Clay]]. [[avalyse-scripts-cold-outreach-v1]]
- **Integração de CRM:** Clientes com API aberta no CRM são integrados diretamente via GHL API. Clientes sem API usam página dedicada (nome + celular) que chama a GHL API e cria o contato na subconta — solução em planejamento. LeadConnector nativo do GHL descartado por ineficiência. [[avalyse-contexto-produto-v1]]
- **Restrição estrutural do GHL (2026-06-19):** plano atual suporta 3 subcontas (1 reservada para uso próprio = **máximo 2 clientes simultâneos**). Upgrade para subcontas ilimitadas custa ~R$1.500/mês. Gatilho de upgrade: MRR ≥ R$1.500 (~4 clientes). Até lá, onboarding é manual e deliberadamente limitado — o teto de capacidade é um buffer de qualidade, não um bloqueio. Onboarding automatizado é prioridade *após* o upgrade, não antes.[[thinking-in-systems-avalyse]]]
- **Objetivo 3 meses (até 2026-07-15):** 1° cliente pagante + início do desenvolvimento da plataforma própria em código. [[avalyse-contexto-produto-v1]] — **faltam 21 dias** (2026-06-24). Ver [[analyses/deadline-primeiro-cliente-2026-07-15]].
- **Dados de execução (até 2026-06-25):** ~407 msgs disparadas acumulado. Quebra-gelo: 12,6% resposta (acima do benchmark 8%). Follow-up: 55,6% resposta. **1 trial ativo** (Hey Peppers, escola, RS — início 26/06, 7 dias). 0 clientes pagantes. Academias SP confirmado como nicho ruim (1,2% resposta). Óticas ABC: 56% resposta mas 0 convertidos — gargalo pós-resposta. Ban em 22/06 pausou toda a prospecção. Ver [[analyses/metricas-execucao-avalyse]].
- **Meta fim de 2026:** R$30k MRR. Ao pricing atual, ~50–75 clientes. [[contexto-thiago-chamlian]]
- **Fundador:** [[thiago-ccuri]], 17 anos, estudante — janelas de trabalho fora de seg–sex 7:25–16:00. Runway R$10k, sustentado pelos pais. [[contexto-thiago-chamlian]]
- **Negócio anterior:** [[denarius-wd]] (agência de marketing ticket alto) — encerrou sem clientes. Mesma trava de aquisição está sendo enfrentada na Avalyse. [[contexto-thiago-chamlian]]

## Nichos — mapeamento de outreach

### Já prospectados (abr/2026)
| Nicho | Avaliação | Motivo |
|---|---|---|
| Clínica odontológica | ⚠️ Médio | Alta dor, ticket alto; ciclo de decisão mais longo (possíveis sócios) |
| Clínica estética | ✅ Melhor testado | Alta dor, ticket médio-alto, dono decide sozinho, WA nativo |
| Salão de beleza | ⚠️ Médio | Volume alto, mas ticket baixo gera objeção de preço no R$397/mês |
| Loja de móveis | ❌ Frio | Volume de clientes baixo; nota 5.0 = sem dor imediata percebida |

### Sugeridos para testar
| Nicho | Avaliação | Motivo |
|---|---|---|
| Oficina mecânica | ✅ Prioritário | Desconfiança estrutural do setor = dor mais aguda; ticket R$300–3k; dono decide; WA nativo |
| Clínica veterinária | ✅ Alto potencial | Alta carga emocional; review negativo = devastador; dono sensível |
| Academia de ginástica | ❌ Testado — ruim | 168 msgs disparadas, 1,2% resposta, 0 convertidos (jun/2026) |
| Escola de idiomas / habilidades | ⚠️ Em teste | Hey Peppers (Niqui Lang, RS) — franquia de 31 unidades; alunos entram continuamente; pais pesquisam no Google antes de matricular. Incógnita: gatilho do WhatsApp (pós-matrícula? pós-aula inaugural?) precisa ser definido no onboarding. Se funcionar → potencial de indicação para outras franqueadas. |

### Evitar por agora
| Nicho                | Motivo                                                                                  |
| -------------------- | --------------------------------------------------------------------------------------- |
| Restaurante / bar    | Margem baixa, dono sobrecarregado, churn alto, sem coleta de forma de numero de celular |
| Farmácia             | Apenas 8% de influência de avaliações no setor (pesquisa Harmo 2025)                    |
| Loja de departamento | Grande demais — decisor não é o dono                                                    |

### Filtros de qualificação obrigatórios antes de qualquer demo
1. **Coleta número de celular dos clientes?** — sem isso o produto não funciona
2. **Nota entre 3.5–4.4?** — zona de dor real e percebida
3. **Mínimo 30 avaliações?** — garante volume suficiente para o produto gerar resultado visível
4. **Dono é o decisor?** — ciclo de venda curto
5. **Atendimento presencial com fluxo contínuo de clientes?** — justifica automação

## Concorrentes

| Concorrente    | Origem | Diferença                                                      |
| -------------- | ------ | -------------------------------------------------------------- |
| Harmo          | BR     | Foco em grandes redes; sem WhatsApp como canal principal       |
| Podium         | EUA    | Email/SMS; preço em dólar                                      |
| Birdeye        | EUA    | Suite completa; complexidade e preço alto                      |
| Nice Job       | EUA    | Foco em contratistas; sem filtragem                            |
| Review Harvest | EUA    | Principal inspiração                                           |
| Reviewly.ai    | EUA    | SMS como canal; posicionamento anti-filtragem; inbound via SEO |

## Materiais de Vendas

| Material | Status | Descrição |
|---|---|---|
| **Apresentação Canva** | ✅ Existe | Slides usados durante o pitch na reunião de demo. Cobre: automação de mensagens, filtro de reviews, respostas automáticas, engajamento no Instagram. Apresentado com compartilhamento de tela no Zoom. |
| **Script de Sales Call** | ✅ Existe | Roteiro completo da reunião de demo. Estrutura: (1) Abertura — rapport + cutucada na dor + perguntas de diagnóstico; (2) Pitch — demo via Canva + prova social Review Harvest + preços; (3) CTA — integração na hora ou agendamento de onboarding. Arquivo: `raw/avalyse-demo-meeting-script-v1.md` |
| **Script de Onboarding** | ❌ Não criado | Roteiro para a sessão de setup técnico (~20min): criação de subconta no GHL, integração WhatsApp + Instagram + Google Meu Negócio, configuração do workflow. A ser desenvolvido. |

## Appearances

[[sources/avalyse-scripts-cold-outreach-v1]],[[avalyse-contexto-produto]]], [[sources/contexto-thiago-chamlian]], [[avalyse-cold-call-scripts]], [[sources/avalyse-demo-meeting-script-v1]], [[estrutura-cold-call-v3]],[[validacao-e-primeiro-cliente]]]

## Related

[[thiago-ccuri]], [[denarius-wd]], [[whatsapp-bulker]], [[Clay]], [[MapRanking]], [[Whitespark]], [[reputacao-online]], [[google-meu-negocio]], [[prova-social]], [[lead-magnet]], [[Outreach]], [[GoHighLevel]], [[filtragem-de-avaliacoes]], [[review-gating]], [[bootstrapping-saas]], [[ativo-silencioso]], [[flywheel-reputacao-conteudo]], [[tracks-prospecao]]
