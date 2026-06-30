---
title: "Cold Call V3 — Script e Sistema de Execução"
type: analysis
tags: [vendas, cold-call, scripts, execucao, avalyse, outreach]
created: 2026-06-08
updated: 2026-06-08
sources: 2
---

## Contexto

Design aprovado em sessão de brainstorming em 2026-06-08. Baseia-se nos scripts [[avalyse-cold-call-scripts]] (V1 e V2) e incorpora nova vantagem técnica: lookup CEP → CNPJ → nome do sócio com ~90% de precisão. Objetivo duplo: script V3 nativo para a nova mecânica + sistema de execução que elimina call reluctance pré-discagem.

---

## Script V3

### Mecânica central

O nome do dono é a **abertura**, não um detalhe. Em V1/V2, o FASE 1 pedia "o responsável pelo negócio" — genérico, sinaliza vendedor frio. Em V3, você pede pelo nome. A secretária não precisa mais qualificar você; o tom é de quem conhece a casa.

---

### FASE 1 — Gatekeeper

**Abertura padrão:**
> Oi, tudo bem? Aqui é o Thiago. O **[Nome do Dono]** está disponível?

**Ramificações:**

| Situação | Resposta |
|---|---|
| Passa direto | → FASE 2 |
| "É sobre o quê?" | "É sobre uma análise que eu rodei do perfil de vocês no Google Maps — queria passar direto pra ele." |
| "Tá ocupado" | "Sem problema. Quando seria um bom horário para eu ligar de volta?" *(pede hora específica)* |
| Nome errado (~10%) | "Me desculpe, pode ser que minha informação esteja desatualizada — quem seria o responsável pelo negócio?" → anota o nome correto, continua |

---

### FASE 2 — Dono

**Abertura:**
> [Nome do Dono], aqui é o Thiago da Avalyse. Vou ser direto: rodei uma análise do [Nome do Negócio] no Google Maps hoje cedo e produzi um relatório que achei que valia te mostrar. Você tem dois minutinhos?

**Diagnóstico:**
> Então [Nome] — hoje quando alguém busca "[nicho] em [bairro]" no Maps, o [Nome do Negócio] aparece em média na [X]ª posição. Os 3 primeiros resultados concentram quase 75% de todos os cliques. O grande fator por trás das primeiras posições é um só: avaliações online — nota média, frequência, quantidade, comentários.
>
> Me ajuda a entender uma coisa: vocês têm algum processo para receber avaliações dos clientes hoje?

**Se não tiver processo:**
> Faz total sentido [Nome] — é assim na maioria dos negócios. E é exatamente aí que mora a oportunidade.

**Se tiver processo:**
> Show — já é muito melhor que a maioria.

**Prova social + CTA:**
> O que a gente faz é levar um passo além: automatizar o processo por completo — solicitações, respostas a comentários, gerenciamento.
>
> Nos EUA, uma ferramenta semelhante à Avalyse fez uma pet care ir de 194 para 240+ avaliações em 2 semanas — 46 avaliações novas em 14 dias.
>
> Vou ser honesto: a Avalyse tá em fase de validação no Brasil — por isso os primeiros 7 dias são grátis, sem cartão. Eu preciso de feedback de donos como você tanto quanto você precisa do resultado.
>
> O que eu te proponho: 10 minutos no Zoom, te mostro como funcionaria especificamente para o [Nome do Negócio]. Se fizer sentido, você testa 7 dias grátis. Se não, a gente se despede.
>
> Você consegue **[dia] às [hora]** ou **[dia] às [hora]**?

---

### Mapa de objeções (herdado do V2)

| Objeção | Resposta |
|---|---|
| "Manda por WhatsApp" | "Claro, posso mandar. Mas seria muito mais rico te mostrar ao vivo — são 10 minutos. Você teria [dia] às [hora]?" |
| "Vou avaliar" | "Faz sentido. Para facilitar — se eu reservar [dia] às [hora] por 10 minutos, você consegue dar uma olhada antes e já vir com as dúvidas?" |
| "Quanto custa?" | "Antes de falar de preço, quero te mostrar o que a ferramenta faz pelo seu negócio especificamente — aí o número faz mais sentido. São 10 minutos. Você teria [dia]?" |
| "Não tenho interesse" | "Entendo [Nome]. Posso te perguntar — o que te fez dizer isso? É o timing, ou tem algo específico no que eu disse?" *(calibrated question — Voss)* |

---

## Sistema de Execução

### Bloco fixo de calls

**Horário principal:** 16h30–17h30, todo dia útil após a escola.
**Janela de reposição:** 20h–20h30 (para negócios com funcionamento noturno ou celular do dono).
**Regra:** Lista aberta antes de sentar. Headphones. Primeira call sem pausa para pensar.

A decisão de ligar acontece uma vez — quando você define o bloco. Durante o bloco, você não decide nada; executa.

---

### Rampa progressiva

| Semana | Calls/dia | Total semanal | Objetivo da semana |
|--------|-----------|----------------|-------------------|
| 1 | 3 | ~15 | Fluência no script, sem pressão de resultado |
| 2 | 5 | ~25 | Gatekeeper fluindo, FASE 2 sem travar |
| 3 | 8 | ~40 | Primeira(s) reunião(ões) marcada(s) |
| 4 | 15 | ~75 | Volume real, funil previsível |

O nervosismo pré-discagem dissolve em torno da call 30–40 acumulada. A rampa existe para chegar lá sem queimar.

---

### Tracking mínimo

Uma linha por dia:

| Data | Calls | Gatekeeper passou | Dono atingido | Reunião marcada |
|------|-------|-------------------|---------------|-----------------|

Nada mais. Objetivo das semanas 1–2: **volume e fluência**, não reuniões. Reuniões são consequência.

---

### Regra inquebrável

Se perdeu o bloco das 16h30 → janela de reposição às 20h.
Se perdeu as duas → dia conta como zero. Sem negociação, sem "compensa amanhã".

A planilha é o antídoto para o medo de terminar mais um ciclo sem resultado — o dado está lá toda noite.

---

## Notas técnicas

- **Nome errado (~10%):** não abortar a call — anotar o nome correto e continuar com o script padrão. O fato de ter tentado pesquisar já sinaliza diligência.
- **Dado dos 75% de cliques:** fonte qualitativa confirmada via comportamento de busca; usar com confiança.
- **Dado "1/4 da influência":** baseado no [[sources/whitespark-local-ranking-factors-2026]] — avaliações = ~21% do total. Usar "quase 1/4" é defensável.
- **Prova social EUA:** manter a declaração explícita "ferramenta semelhante nos EUA" — não atribuir como cliente Avalyse.

---

## Relacionados

[[avalyse-cold-call-scripts]], [[concepts/outreach]], [[concepts/negociacao-voss]], [[entities/avalyse]], [[concepts/seo-local]], [[plano-30-dias-avalyse-encerrado]]
