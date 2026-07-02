# Fluxo de Outbound — Curiosity Gap + Demo Gate (Fase 1: WhatsApp) Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Produzir o conteúdo real (textos + roteiro de vídeo) da sequência de WhatsApp definida em `docs/superpowers/specs/2026-07-01-outbound-curiosity-gap-design.md`, pronto para colar no WhatsApp Bulker e para gravação do vídeo fixo.

**Architecture:** Cada etapa do fluxo (curiosity gap, mensagem personalizada, vídeo, CTA de demo, follow-up) é um arquivo de conteúdo independente em `content/outbound/whatsapp-curiosity-gap-v1/`, revisado contra as regras do gate antes de ser considerado pronto para uso.

**Tech Stack:** Markdown puro (conteúdo de copy); nenhuma dependência de software. Verificação de regras via `grep` sobre os arquivos de texto.

## Executor

Alex Hormozi. Todo o copy escrito nas tasks abaixo (curiosity gap, mensagem personalizada, roteiro de vídeo, CTA de demo, follow-up) é rascunho de referência, não texto travado — o executor tem liberdade para reescrever qualquer mensagem de acordo com seu próprio filtro e estilo, desde que as Global Constraints abaixo sejam respeitadas (gate, termos proibidos, personalização).

## Global Constraints

- Nunca mencionar "avaliação", "avaliações", "review", "reviews" ou "SEO" em qualquer texto/vídeo anterior à demo (regra do gate — spec §Passo 3/4).
- Nenhuma peça pré-demo pode entregar o diagnóstico completo (ranking, SEO, site, bullet points) — só a existência dele.
- Toda mensagem personalizada usa os tokens `{Nome}` e `{Negocio}` (não hardcodear nomes de exemplo fora de comentários).
- Segmentação/ICP não mudam (fora de escopo deste plano — ver spec).
- Cold call (Fase 2 no design original) entra aqui **só como follow-up de reengajamento**, não como canal de entrada próprio — canal de entrada por voz fica para depois.

---

### Task 1: Quebra-gelo (reuso do v3 — sem mudança)

**Files:**
- Nenhum arquivo novo. O quebra-gelo já existe no funil v3 (`wiki/concepts/outreach.md`, seção "Aplicação real: cold outreach B2B local (WhatsApp)").

**Interfaces:**
- Produces: nada novo — ponto de entrada do fluxo continua igual.

- [ ] **Step 1: Confirmar que as 3 variantes anti-ban do quebra-gelo v3 continuam válidas**

Abrir `wiki/concepts/outreach.md` e localizar a seção do quebra-gelo v3. Nenhuma mudança de copy é necessária — este task só existe para deixar explícito que o fluxo novo herda essa etapa sem alteração.

- [ ] **Step 2: Marcar como confirmado**

Nenhum commit necessário (nenhum arquivo mudou).

---

### Task 2: Mensagem de contexto + curiosity gap (Passo 2)

**Files:**
- Create: `content/outbound/whatsapp-curiosity-gap-v1/02-curiosity-gap.md`

**Interfaces:**
- Consumes: resposta positiva ao quebra-gelo (Task 1).
- Produces: duas variantes de mensagem (A e B) para teste A/B — a variante escolhida no teste alimenta o Task 3 (mensagem personalizada é a resposta a esta etapa).

- [ ] **Step 1: Escrever o arquivo com as duas variantes**

```markdown
# Passo 2 — Curiosity Gap

Enviado depois que o lead responde ao quebra-gelo.
Teste A/B: metade da base recebe Variante A, metade recebe Variante B.

## Variante A — gap direto

Oi {Nome}! Separei um raio-x rápido do perfil de {Negocio} no Google e achei um ponto que imagino que vocês nem sabem que tá acontecendo. Faz sentido eu te mostrar?

## Variante B — pergunta de contexto antes do gap

Oi {Nome}! Rapidinho — hoje, quando um cliente novo pesquisa {Negocio} no Google antes de decidir onde ir, você sabe o que ele vê primeiro?

(aguardar resposta)

Fiz um raio-x rápido do perfil de vocês e achei um ponto que imagino que vocês nem sabem que tá acontecendo. Faz sentido eu te mostrar?

## Critério de sucesso do teste

Métrica: taxa de resposta positiva (aceita ver o raio-x) por variante, sobre o total que respondeu o quebra-gelo. Rodar por pelo menos 100 envios por variante antes de declarar vencedora.
```

- [ ] **Step 2: Verificar que nenhuma palavra proibida aparece**

Run: `grep -inE "avalia|review|seo" "content/outbound/whatsapp-curiosity-gap-v1/02-curiosity-gap.md"`
Expected: nenhuma saída (exit code 1 / sem matches, ignorando a linha de metadados "Critério de sucesso" que não contém essas palavras).

- [ ] **Step 3: Verificar que os tokens de personalização estão presentes nas duas variantes**

Run: `grep -c "{Nome}" "content/outbound/whatsapp-curiosity-gap-v1/02-curiosity-gap.md"`
Expected: `2` (uma ocorrência por variante)

- [ ] **Step 4: Commit**

```bash
git add content/outbound/whatsapp-curiosity-gap-v1/02-curiosity-gap.md
git commit -m "Add curiosity-gap message variants for outbound WhatsApp flow"
```

---

### Task 3: Mensagem personalizada + roteiro do vídeo fixo (Passo 3)

**Files:**
- Create: `content/outbound/whatsapp-curiosity-gap-v1/03-mensagem-personalizada.md`
- Create: `content/outbound/whatsapp-curiosity-gap-v1/03-video-roteiro.md`

**Interfaces:**
- Consumes: resposta positiva ao curiosity gap (Task 2).
- Produces: template de mensagem (consumido no envio real) + roteiro de vídeo (consumido na gravação manual, fora deste plano — gravação é ação humana, não automatizável).

- [ ] **Step 1: Escrever a mensagem personalizada**

```markdown
# Passo 3 — Mensagem Personalizada (acompanha o vídeo fixo)

Show, {Nome}! Gravei um vídeo rapidinho (2 min) mostrando o que eu quis dizer com o raio-x do perfil de {Negocio} — dá uma olhada:

{link_video}

[anexar/enviar junto com o vídeo fixo no mesmo envio]
```

- [ ] **Step 2: Escrever o roteiro do vídeo fixo**

```markdown
# Roteiro — Vídeo Fixo (genérico, reaproveitável)

Duração alvo: 90-120 segundos. Visual dinâmico (tela + texto na tela), não fala parada.
Regra: falar em takeaways/outcomes, nunca no mecanismo (não citar "avaliação", "review", "SEO", "ranking" tecnicamente).

## Cena 1 (0-15s) — Gancho
Fala: "Toda vez que alguém pesquisa o nome de um negócio no Google antes de decidir se vai comprar, tem 3 coisas que definem se essa pessoa aparece ou desaparece pro concorrente."
Tela: título "O que decide se o cliente escolhe você ou o concorrente"

## Cena 2 (15-45s) — O que o raio-x entrega
Fala: "Eu fiz um raio-x do perfil de vocês no Google e separei três coisas: onde vocês estão posicionados hoje na busca, os pontos específicos que estão te fazendo perder espaço, e um site novo — feito com IA, sem custo — pra fechar os buracos que encontrei."
Tela: 3 bullet points animados: "Posição atual", "Pontos de melhoria", "Site novo grátis"

## Cena 3 (45-75s) — Prova de que é real e específico
Fala: "Não é genérico — é o perfil de vocês, com os números de vocês. Só dá pra entender o impacto completo vendo na tela, então separei 10 minutos pra te mostrar."
Tela: mockup de tela com gráfico/relatório desfocado (sugerindo conteúdo real sem revelar)

## Cena 4 (75-100s) — CTA
Fala: "Se fizer sentido, me chama de volta no WhatsApp e a gente marca os 10 minutos, sem compromisso."
Tela: texto "Responde aqui no WhatsApp pra marcarmos"

## Notas de produção
- Gravação: tela + voz (Thiago), sem necessidade de aparecer no vídeo.
- Ferramenta: qualquer gravador de tela com edição básica de texto sobreposto.
- Este vídeo é ÚNICO e reaproveitável para todos os leads — a personalização fica só na mensagem de texto que o acompanha (Step 1 deste task).
```

- [ ] **Step 3: Verificar que nenhuma palavra proibida aparece no roteiro nem na mensagem**

Run: `grep -inE "avalia|review\b|\bseo\b" "content/outbound/whatsapp-curiosity-gap-v1/03-mensagem-personalizada.md" "content/outbound/whatsapp-curiosity-gap-v1/03-video-roteiro.md"`
Expected: nenhuma saída

- [ ] **Step 4: Commit**

```bash
git add content/outbound/whatsapp-curiosity-gap-v1/03-mensagem-personalizada.md content/outbound/whatsapp-curiosity-gap-v1/03-video-roteiro.md
git commit -m "Add personalized follow-up message and fixed video script"
```

- [ ] **Step 5: Ação manual (fora do plano automatizável)**

Thiago grava o vídeo seguindo o roteiro de `03-video-roteiro.md` e hospeda em um link estável (ex: Google Drive público, YouTube não-listado). Sem essa gravação, Task 4 não pode ser testado ponta a ponta — mas o texto do CTA (Task 4) não depende do vídeo estar gravado para ser escrito.

---

### Task 4: CTA de demo + resposta ao pedido de "manda por texto" (Passo 4 — gate)

**Files:**
- Create: `content/outbound/whatsapp-curiosity-gap-v1/04-cta-demo.md`

**Interfaces:**
- Consumes: resposta ao vídeo+mensagem personalizada (Task 3).
- Produces: texto de CTA (consumido no envio real) + script de recusa do gate (consumido sempre que um lead pedir a versão reduzida por texto).

- [ ] **Step 1: Escrever o CTA de demo**

```markdown
# Passo 4 — CTA de Demo

Enviado logo após o vídeo (Task 3), pode ser a mesma mensagem ou a próxima, dependendo do teste A/B do passo 2 (ver nota abaixo).

## CTA

Quer que eu te mostre tudo isso ao vivo — a posição de vocês, os pontos específicos de melhoria e o site novo? Consigo em 10 minutos, sem compromisso. Prefere hoje ou amanhã?

## Regra do gate — resposta padrão se o lead pedir "manda por texto"

Entendo! Mas o raio-x completo tem uns pontos visuais que ficam bem mais claros mostrando na tela — em 10 minutos você já sai sabendo exatamente onde estão as oportunidades, sem enrolação. Prefere hoje à tarde ou amanhã de manhã?

## Regra do gate — se insistir uma segunda vez

Sem problema te entender a preferência, mas esse é o formato que funciona de verdade — 10 minutos e você já sai com a resposta. Fica pra quando fizer sentido pra você, é só me chamar.

(Não enviar nenhum dado do diagnóstico completo por texto, mesmo após segunda recusa — encerrar a insistência sem ceder o gate, per spec §Passo 4.)
```

- [ ] **Step 2: Verificar que a resposta ao gate não cede nenhum dado do diagnóstico**

Run: `grep -inE "posição.*[0-9]|ranking.*[0-9]|nota [0-9]" "content/outbound/whatsapp-curiosity-gap-v1/04-cta-demo.md"`
Expected: nenhuma saída (confirma que nenhum número/dado real do diagnóstico foi escrito no texto de recusa)

- [ ] **Step 3: Commit**

```bash
git add content/outbound/whatsapp-curiosity-gap-v1/04-cta-demo.md
git commit -m "Add demo CTA and hard-gate refusal script"
```

---

### Task 5: Follow-up via cold call (Passo 5 — decidido em 2026-07-01)

**Files:**
- Create: `content/outbound/whatsapp-curiosity-gap-v1/05-followup-cold-call.md`

**Interfaces:**
- Consumes: nenhuma resposta após CTA de demo (Task 4) por 24-48h.
- Produces: script de abertura de ligação (consumido pelo rep — Thiago — ao discar).

- [ ] **Step 1: Escrever o script de abertura da ligação de follow-up**

```markdown
# Passo 5 — Follow-up via Cold Call

Decisão de 2026-07-01: sem resposta ao vídeo/CTA por 24-48h, o follow-up escala
para ligação (não mais mensagem de texto). Roteiro detalhado de cold call como
canal de entrada próprio (Track 2) fica para Fase 2 — este script cobre apenas
a abertura de reengajamento.

## Abertura (fecha o gap de confiança em ~7 segundos)

"Oi, {Nome}? Aqui é o Thiago — te mandei uma mensagem no WhatsApp com um vídeo
sobre um raio-x que separei do perfil de {Negocio} no Google, não sei se chegou
a ver. Tem 2 minutinhos agora?"

## Se disser que sim (tem 2 minutos)

"Show. Basicamente eu separei três coisas específicas sobre a posição de vocês
na busca — e tem um ponto que imagino que vocês nem sabiam que tava acontecendo.
Prefiro te mostrar na tela porque fica bem mais claro — consigo em 10 minutos,
hoje ou amanhã?"

## Se disser que não é um bom momento

"Sem problema! Te ligo em outro horário — prefere de manhã ou de tarde?"

(Se recusar novamente após 2ª tentativa de ligação: mover lead para lista de
reengajamento futuro, não insistir uma 3ª vez.)
```

- [ ] **Step 2: Verificar que o script não revela dados do diagnóstico nem termos proibidos**

Run: `grep -inE "avalia|review\b|\bseo\b|posição [0-9]|nota [0-9]" "content/outbound/whatsapp-curiosity-gap-v1/05-followup-cold-call.md"`
Expected: nenhuma saída

- [ ] **Step 3: Commit**

```bash
git add content/outbound/whatsapp-curiosity-gap-v1/05-followup-cold-call.md
git commit -m "Add cold-call follow-up script for unresponsive WhatsApp leads"
```

---

### Task 6: Carregar os textos no WhatsApp Bulker e ativar o teste A/B do Passo 2

**Files:**
- Nenhum arquivo de código — ação operacional na ferramenta `whatsapp-bulker` (ver `wiki/entities/whatsapp-bulker.md`).

**Interfaces:**
- Consumes: todos os arquivos de `content/outbound/whatsapp-curiosity-gap-v1/`.
- Produces: campanha ativa no Bulker rodando o novo fluxo.

- [ ] **Step 1: Cadastrar os templates das Tasks 2-5 no WhatsApp Bulker**

Copiar o conteúdo de cada arquivo `.md` (sem os cabeçalhos de documentação) para os templates de mensagem do Bulker, substituindo `{Nome}` e `{Negocio}` pelos campos reais de merge da ferramenta.

- [ ] **Step 2: Configurar o split A/B do Passo 2**

Metade da lista ativa recebe a Variante A, metade recebe a Variante B (Task 2). Confirmar no Bulker que o split é aleatório e balanceado, não sequencial.

- [ ] **Step 3: Rodar por pelo menos 100 envios por variante e registrar o resultado**

Sem commit — este é um dado operacional, não um artefato de código. Quando houver volume suficiente, atualizar `wiki/analyses/gargalo-conversao-outreach.md` via protocolo semanal (`NEW DATA`) com a variante vencedora e a taxa de resposta observada.

---

## Self-Review

**Spec coverage:** Task 1 (quebra-gelo, sem mudança) · Task 2 (curiosity gap, variantes A/B) · Task 3 (mensagem personalizada + vídeo) · Task 4 (CTA de demo + gate rígido) · Task 5 (follow-up via cold call, decisão de 2026-07-01) · Task 6 (ativação operacional + medição). Todas as seções da spec `2026-07-01-outbound-curiosity-gap-design.md` têm uma task correspondente. Produção do vídeo (gravação) e reescrita do script da demo continuam fora de escopo, como definido na spec.

**Placeholder scan:** nenhum "TBD"/"TODO" — todo texto de copy é final, pronto para uso. A única ação manual não automatizável (gravação do vídeo) está marcada explicitamente como tal no Task 3, Step 5, e não bloqueia os demais tasks.

**Type consistency:** tokens de personalização (`{Nome}`, `{Negocio}`) usados de forma consistente em todos os arquivos de Task 2 a 5.
