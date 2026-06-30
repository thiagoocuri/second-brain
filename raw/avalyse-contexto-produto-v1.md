# Avalyse — Contexto de Produto, Mercado e Operações v1

> Coletado em 2026-04-15. Fonte: Thiago Ccuri (fundador).
> Informações sobre produto, tech stack, concorrência, pricing, funil e objetivos.

---

## Tech Stack

- Plataforma base: GoHighLevel (GHL)
- WhatsApp integrado via API oficial
- Dashboard completo de desempenho de avaliações
- CRM nativo: LeadConnector (GHL)
- Ferramentas externas: MapRanking (diagnóstico manual de ranking no Google Maps)

## O que é automatizado vs. manual

**Manual (setup por cliente):**
- Criar subconta do cliente no GHL
- Integrar WhatsApp do cliente
- Integrar Instagram do cliente
- Integrar Google Meu Negócio (GMB) do cliente
- Integrar CRM nativo do cliente (quando aplicável)

**Automatizado (pós-setup):**
- Envio de mensagem WhatsApp pós-atendimento
- Redirecionamento para subpágina de filtragem
- Resposta automática às avaliações recebidas
- Compartilhamento nos Stories do Instagram

## Sistema de Filtragem de Avaliações

Diferencial técnico central. O link enviado ao cliente final não vai direto ao Google — vai para uma subpágina com 4 emojis:
- 2 emojis positivos → redirecionam para o Google (avaliação pública)
- 2 emojis negativos → redirecionam para formulário interno (feedback privado, só o dono vê)

Efeito: filtra avaliações negativas antes de chegarem ao Google, aumenta nota média e protege reputação.

## Limitações Conhecidas

- Dificuldade em integrar o CRM nativo do cliente com o LeadConnector do GHL

## Concorrência

**Brasil:**
- Harmo (líder local, foco em grandes redes)

**Internacional:**
- Podium, Birdeye, Nice Job, Review Harvest

**Diferencial da Avalyse:**
- Canal WhatsApp (concorrentes usam email/SMS — menor taxa de abertura no BR)
- Flexibilidade de opcionais configuráveis pelo cliente
- Sistema de filtragem de avaliações (emojis → roteamento positivo/negativo)
- Setup completo em reunião de 20min

## ICP

Prestadores de serviço locais com atendimento presencial e dependência de visibilidade no Google Maps:
- Salões de cabeleireiro
- Clínicas estéticas
- Clínicas odontológicas
- Lojas de móveis
- Prestadores de serviço local em geral

**Decisor:** sempre o dono do negócio.

## Funil de Vendas

1. Cold outreach WhatsApp (scripts v1)
2. Reunião de até 20 minutos (demo)
3. Pergunta de fechamento imediato: "Quer prosseguir?"
4. Se sim: cria subconta + configura tudo na mesma sessão (onboarding imediato)

**CRM:** pipeline no GHL mostrando estágio de cada lead/cliente.

**Principal objeção identificada:** "o cliente vê a mensagem e ignora."

## Prova Social

- Não tem clientes próprios ainda (fase de validação)
- Tem prova social de negócios que usaram método similar com resultados extraordinários (não especificados)

## Pricing (não definitivo)

| Plano | Preço/mês | Volume de avaliações |
|---|---|---|
| Básico | R$397 | 0–30/mês |
| Pro | R$597 | 30–60/mês |
| Max | Sob consulta | 60+/mês |

Referência de precificação: comparação com concorrentes internacionais.

## Operações

- Time: solo founder (Thiago). Possibilidade de contratar alguém para tarefas menores (não garantido).
- Diagnóstico de ranking: feito manualmente via MapRanking
- Volume de outreach: a definir conforme automações disponíveis

## Objetivos (3 meses — até 2026-07-15)

1. Validar produto (1° cliente pagante)
2. Iniciar desenvolvimento da plataforma oficial com código próprio (saindo do GHL)
