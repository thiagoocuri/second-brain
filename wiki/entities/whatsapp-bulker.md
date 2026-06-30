---
title: WhatsApp Bulker
type: entity
tags:
  - product
  - tool
  - internal
  - avalyse
created: 2026-04-21
updated: 2026-06-24
sources: 0
---

## Overview
Ferramenta interna da [[entities/avalyse]] para disparos de WhatsApp em massa com proteções anti-ban. Roda em VPS própria — uso exclusivo interno, não é um produto SaaS.

## Stack

| Camada    | Tecnologia                                      |
|-----------|-------------------------------------------------|
| Backend   | Node 20 · Fastify · TypeScript · Baileys (lib WA unofficial) |
| Banco     | SQLite via Prisma (produção no VPS)             |
| Frontend  | Next.js 15 · Tailwind CSS                      |
| Deploy    | Docker Compose + Caddy · VPS `187-127-25-82.sslip.io` |

## Como Funciona
- Contatos importados via CSV, organizados em listas e marcados com tags
- Campanhas apontam para uma lista + template(s), têm filtros por tag/status, e ficam em fila
- Worker (`worker.ts`) processa a fila com delays randômicos, limites diários e quiet hours
- Baileys conecta ao WhatsApp via multi-device (QR code no terminal) e faz os envios
- Dashboard (Next.js) permite gerenciar tudo via browser

## Proteções Anti-Ban
- **Warmup:** primeiros 14 dias sobem o limite gradualmente (10 → 60 msgs/dia)
- **Delay randômico:** mínimo 5 min entre envios
- **Template rotation:** mínimo 3 templates por campanha (sorteados aleatoriamente)
- **Quiet hours:** sem envios entre 22h–8h nem domingos
- **Opt-out automático:** SAIR/PARAR/CANCELAR → blacklist imediata

## Features

### Implementadas
- Follow-up automático: quando lead responde pela 1ª vez, aguarda 30s e envia template de follow-up configurado na campanha — bypassa caps e quiet hours
- LID Cache persistence (jun/2026): resolve lid → phone e persiste o mapeamento no banco para sobreviver a restarts (necessário porque WA usa JIDs de privacidade `@lid` nas mensagens recebidas)
- Bulk delete de contatos
- Export CSV nativo
- Import CSV por lista
- Formulário dedicado por cliente (jun/2026): página externa ao GHL com rota/credencial isolada por cliente — funcionário preenche nome + celular, GHL API cria o contato na subconta correta e dispara o workflow. Resolve o modo "Sem API" do produto.

## Status
Produção completa — todas as fases (0–7) implementadas.

## Limite operacional real

Ban ocorre quando o volume ultrapassa o threshold do WhatsApp. O cap teórico pós-warmup é 60 msgs/dia, mas o limite empírico seguro ainda está sendo calibrado.

**Incidentes registrados:**
| Data | Duração | Impacto |
|------|---------|---------|
| jun/2026 (anterior) | ~2h | — |
| 2026-06-22 | em andamento (tentativa retorno 2026-06-24) | prospecção 100% pausada |

Ver [[anti-ban-whatsapp]] para opções de escala.

## Related
[[entities/avalyse]], [[concepts/outreach]]
