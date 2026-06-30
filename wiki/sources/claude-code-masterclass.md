---
title: "Claude Code Masterclass — Agentes, Skills e Workflows em Produção"
type: source
tags: [claude-code, ai, agentes, skills, contexto, automacao, youtube]
created: 2026-04-18
updated: 2026-06-22
raw:
  - "raw/how-ai-agents-claude-skills-work.md"
  - "raw/CLAUDE CODE MASTERCLASS.md"
creators:
  - "[[ross-mike]]"
  - "[[michele-torti]]"
---

## Summary

Combinação de duas fontes complementares sobre Claude Code e agentes de IA: podcast com [[ross-mike]] (desenvolvedor especializado em agentes de IA) e masterclass de 4 horas de [[michele-torti]] (fundador de agência de automação 6 figures, 10.000+ alunos).

**Tese compartilhada:** os modelos LLM já são bons o suficiente — o diferencial está na qualidade do **contexto** fornecido. Quem domina o setup (CLAUDE.md, skills, MCPs, sub-agentes) obtém outputs 10× melhores do que quem vai direto ao uso.

**Ross Mike** foca na metodologia de construção progressiva: executar workflows manualmente com o agente → converter em skill após execução bem-sucedida → refinamento recursivo. Defende parcimônia com CLAUDE.md e abstinência de skills de terceiros. Audiência-alvo: desenvolvedores construindo agentes autônomos com dados sensíveis em produção.

**Michele Torti** foca na arquitetura completa de um projeto Claude Code: Setup Mode vs Use Mode, [[claude-md]], [[skills-ia]], [[mcp|MCP]], [[hooks-claude]], [[sub-agentes]], [[agent-teams]], deployment e três exemplos de build reais (pipeline de YouTube, landing page Ferrari, pipeline de vendas). Audiência-alvo: criadores de conteúdo e construtores de negócios de automação de IA.

A diferença de foco explica a tensão aparente entre as fontes — elas não contradizem, falam para contextos diferentes.

## Key Claims

**Contexto e qualidade:**
- Os modelos já são bons (Opus, GPT-4o). O problema não é mais o modelo — é o contexto fornecido. [[ross-mike]]
- Loop de 4 passos do agente: entender → planejar → usar ferramentas → output. A qualidade é determinada na etapa "entender". [[michele-torti]]
- Setup Mode vs Use Mode: a maioria pula o Setup (escrever CLAUDE.md, instalar skills, configurar MCPs, criar sub-agentes) e depois estranha por que o Claude é inconsistente. [[michele-torti]]
- Fórmula 0.9^5 = 59%: chains de prompts compostos degradam precisão exponencialmente. Solução: conversas independentes por tarefa + Plan Mode antes de executar. [[michele-torti]]

**Skills:**
- Progressive disclosure: só nome e descrição ficam no contexto (~53 tokens); conteúdo completo carregado só quando necessário. CLAUDE.md de 1.000 linhas gasta ~7.000 tokens por turno; mesma informação como skill gasta ~53. [[ross-mike]]
- Não crie skills do zero. Execute o workflow manualmente com o agente → após execução bem-sucedida, peça ao agente para criar a skill. [[ross-mike]]
- Recursive skill building: quando falhar, identifique o erro, corrija, e mande o agente atualizar o arquivo. ~3–5 iterações para estabilizar. [[ross-mike]]
- 95% das pessoas não precisam de CLAUDE.md extenso. Único uso válido: informação proprietária necessária em todo turno. [[ross-mike]]
- Não baixe skills de terceiros: risco de segurança (vetor de ataque) + o agente não tem contexto da execução bem-sucedida do criador original. [[ross-mike]]
- Skill Creator (meta-skill oficial da Anthropic): descreva o workflow, gera o arquivo completo em ~5 minutos. Catálogo ai.tmpl.com com 683+ skills disponíveis. [[michele-torti]]

**Sub-agentes e Agent Teams:**
- Sub-agentes não se comunicam entre si — resultados retornam ao agente principal. Para tasks onde output de A informa B, use Agent Teams. [[michele-torti]]
- Agent Teams têm custo real: ~$80 em build complexa com 4 agentes. Use sub-agentes para paralelização simples; reserve Agent Teams para comunicação inter-agente essencial. [[michele-torti]]
- MCP custa contexto: 2 MCPs consomem ~10.800 tokens automaticamente. Limite: 2–3 MCPs simultâneos. [[michele-torti]]
- Sequência correta de escala: 1 agente → skills estabilizadas → sub-agentes por domínio com volume suficiente. [[ross-mike]]

**Deployment:**
- Quatro plataformas: [[Modal]] (burst/Python, $30 créditos grátis, pay-per-second), [[Railway]] (24/7 via GitHub, $1/mês), [[Render]] (flat billing, $7/mês), [[Replit]] (browser, tier gratuito). [[michele-torti]]
- Deployment sem código manual: Claude cria `modal_app.py`, faz push, configura schedule. Debugging: copiar erro dos logs → colar no Claude Code → Claude corrige → redeploy. [[michele-torti]]

## Entities

[[ross-mike]], [[michele-torti]], [[Modal]], [[Railway]], [[Render]], [[Replit]], [[Vercel]], Anthropic

## Concepts

[[skills-ia]], [[context-window]], [[agentes-ia]], [[sub-agentes]], [[progressive-disclosure]], [[claude-md]], [[mcp]], [[hooks-claude]], [[agent-teams]], [[three-layer-architecture]], [[plan-mode]], [[spec-todo-build]]

## Contradictions & Tensions

- **CLAUDE.md:** Ross Mike (95% não precisam; usar com parcimônia) vs Michele Torti (arquivo mais importante do projeto; sempre criar). Tensão explicável por contexto: Ross Mike fala de agentes autônomos com dados sensíveis; Torti fala de workflows de conteúdo com menor superfície de risco.
- **Skills de terceiros:** Ross Mike (nunca baixe — risco de segurança + falta de contexto de execução) vs Michele Torti (recomenda catálogo ai.tmpl.com com 683+ skills). Tensão não resolvida — critério de triagem ausente.
- **Este vault:** o CLAUDE.md deste Second Brain define workflows proprietários (INGEST, QUERY, LINT) que precisam estar disponíveis em todo turno — exatamente o caso dos 5% que Ross Mike considera válido.

## Open Questions

- Em que ponto o custo de Agent Teams se torna viável para a [[Avalyse]]? A qual MRR faz sentido?
- Como avaliar a segurança de skills de terceiros antes de instalá-las? Existe critério de triagem confiável?
- Como adaptar o método "walk through the workflow" para automações longas onde uma execução completa demora horas?
- Qual é o limite prático de sub-agentes antes de a orquestração prejudicar a performance?
- Progressive disclosure existe nativamente no Claude Code ou depende de como os arquivos são estruturados?
- O pipeline de YouTube do Michele é o mesmo usado para produção real ou é um exemplo simplificado?

---

## Parte I — Metodologia de construção progressiva (Ross Mike)

**Os modelos já são bons.** O problema não é mais o modelo — é o contexto que você dá a ele.

**95% das pessoas não precisam de CLAUDE.md ou agent.md.** O único uso válido é informação proprietária que precisa estar em *todo* turno de conversa.

**Skills usam progressive disclosure:** só nome e descrição ficam no contexto (~53 tokens). O conteúdo completo só é carregado quando o agente identifica que precisa da skill. Um agent.md de 1.000 linhas gasta ~7.000 tokens por turno; a mesma informação como skill gasta ~53.

**Não crie skills direto do zero.** Faça o workflow manualmente com o agente, passo a passo, até ter uma execução bem-sucedida. Só então peça ao agente para converter em skill.

**Recursive skill building:** skills vão falhar. Quando falharem, identifique o erro, corrija, e mande o agente atualizar o arquivo de skill. Repita até estabilizar (~3–5 iterações).

**Não baixe skills de outros.** Risco de segurança (vetor de ataque) e risco de qualidade — o agente não tem o contexto da sua execução bem-sucedida para executar skills de terceiros com fidelidade.

**Escale para produtividade, não para o que parece legal.** Comece com 1 agente. Construa skills para os seus workflows. Só então adicione sub-agentes quando houver workflows suficientes para delegar.

**Contexto window: ótimo entre 0–70%.** Acima de 80–90%, o modelo "fica burro." Economize contexto para manter performance e reduzir custo.

**Templates terão renascimento.** Um template sólido vira contexto para o agente — mais eficaz que um CLAUDE.md genérico.

---

## Parte II — Arquitetura Claude Code (Michele Torti)

### Module 1 — Foundations

**Pricing** — Three tiers. Free: limited usage, enough to test. Pro (~$17/month): recommended starting point. Max (~$100/month): for power users and production workflows. Cost scales with token usage across conversations.

**Hosting options** — Five ways to run Claude Code: VS Code extension, [[Cursor]] IDE, Antigravity IDE (VS Code fork), terminal (most visibility, shows all settings and flags), and the web app. Michele uses the terminal for agent work because it surfaces more context — model, tool use, permissions, memory state.

**Permissions** — Three categories Claude needs approval for: network access (hitting external APIs), browser control (interacting with the web), and file writes/reads. You set defaults in settings.json and override per session. Understand what each permission allows before granting it.

**[[claude-md]]** — The single most important file in any Claude Code project. Think of it as the brain: it holds everything Claude needs to know about the project so it doesn't have to ask. Generated with `/init` on first run. Exists at two levels: global (in `~/.claude/CLAUDE.md`, applies to all projects) and project-level (in the project root, overrides global). Five sections Michele recommends: project context, architecture, core workflows, design decisions, and important context (pitfalls, API quirks, naming conventions).

**The `.claude` directory** — Houses all Claude Code configuration: `CLAUDE.md`, `/commands` (slash command definitions), `/hooks` (trigger scripts), `/mcp.json` (MCP connections), `settings.json` (permissions and model preferences), `/skills` (instruction manuals), `/agents` (sub-agent definitions), `/agent_memory` (persistent agent memory).

**Setup Mode vs Use Mode** — Two distinct phases. Setup Mode: scaffold the project, write CLAUDE.md, install skills, configure MCPs, create sub-agents. Use Mode: actually build and run tasks. Most people jump straight to Use Mode without Setup, and then wonder why Claude is inconsistent. Setup is the multiplier.

**How Claude works** — Four-step loop: understand (read your message + context files) → plan (decide what to do and which tools to use) → use tools (read/write files, run commands, call APIs) → output (return results). The quality of your output is determined at the "understand" step, which is why CLAUDE.md and skills matter so much.

**Models** — Three options:
- **Claude Haiku**: cheapest, fastest. For simple lookups, file reading, quick transformations.
- **Claude Sonnet**: default, balanced. Good for code, writing, most daily tasks. Start here.
- **Claude Opus**: most powerful, most expensive. For hard debugging, complex full-stack builds, anything requiring deep reasoning. Use only when Sonnet fails.

**Context window** — 200,000 tokens per conversation. Every message you send, every response Claude gives, every file it reads, every tool call it makes fills this window. When full, performance degrades. Michele's rule: treat it like a notebook with 200k pages. Don't fill it with trash — start fresh for unrelated tasks.

**Output types** — Text, Markdown (documents, reports), code (files, scripts), and artifacts (interactive HTML/JS widgets previewed in browser).

**Slash commands** — `/init` (generate CLAUDE.md), `/clear` (reset conversation context), `/compact` (summarize context while preserving state), `/context` (show token usage breakdown), `/mcp` (manage MCP servers), `/doctor` (check Claude Code health), `/resume` (continue previous session), `/review` (code review), `/config` (settings).

**Interactive vs headless mode** — Interactive: you're in the loop, Claude asks approval before destructive actions. Headless: Claude runs autonomously without prompts — used for scheduled automation and CI/CD pipelines.

---

### Module 2 — Customization

**[[skills-ia|Skills]]** — Instruction manuals that Claude reads before performing a task. Stored in `.claude/skills/`. Each skill is a folder containing `skill.md` (required) plus optional `references/` and `scripts/`. Without a skill, Claude guesses and gives inconsistent output. With a skill, it follows a pattern every time.

**Installing skills** — Paste the skill URL or code into Claude Code and say "Install this skill." Claude handles the rest. To build manually: create `.claude/skills/<skill-name>/skill.md` with your instructions.

**Skill Creator** — Official Anthropic meta-skill. Describe what you want in plain English, it generates a complete skill file in ~5 minutes. Access via `/manage plugins`.

**Skill evaluation** — `eval.json` defines what good output looks like. `trigger-eval.json` contains 20 test prompts. Run evaluations to benchmark before/after changes — the skill improves itself based on the gap.

**Commands** — Slash command shortcuts stored in `.claude/commands/`. Create a file named `command-name.md` with a description and the skill it should trigger. Now `/command-name` runs the skill without typing instructions.

**[[hooks-claude]]** — Automatic actions that fire on events, regardless of what project you're in. Defined in `settings.json`. Four event types:
1. **Pre-tool use**: runs before Claude uses a tool (e.g., block access to `.env` files)
2. **Post-tool use**: runs after a tool completes (e.g., log every file write)
3. **Stop/notification**: fires when Claude finishes a task (e.g., send a desktop notification)
4. **Post-tool use failure**: fires when a tool call fails (e.g., alert on errors)

**[[mcp|MCP]]** (Model Context Protocol) — Plugins that give Claude new abilities beyond its built-in tools. Configured in `.mcp.json`. Two recommended MCPs:
- **Chrome DevTools MCP**: full browser control — click, fill forms, navigate, take screenshots.
- **Supabase MCP**: vector database connection. Enables semantic search, persistent data, RAG patterns.

Token cost warning: loading two MCPs costs ~10,800 tokens of context automatically. Recommendation: use 2–3 MCPs maximum, and convert stable MCPs into skills when possible to save context.

---

### Module 3 — Prompt Engineering

**Hack 1: Split prompts** — One task per conversation. Chaining compounds errors — each step at 90% accuracy means a 5-step chain is only 59% accurate.

**Hack 2: Plan mode** — For any complex multi-step task, start in plan mode (Shift+Tab toggle). Claude maps out the full plan before writing a single line of code. Review the plan, add comments to refine it, then approve execution.

**Hack 3: Kitchen sink vs clean session** — "Kitchen sink" (one long session with all project context) vs "clean session" (fresh conversation for each unrelated task). Check current usage with `/context`. Rule: start a new conversation when switching to an unrelated task.

**Hack 4: CLAUDE.md as permanent memory** — Every rule you'd otherwise type in every session belongs in CLAUDE.md. Once it's there, Claude always knows it.

**Hack 5: Skills as reusable prompts** — Skills are saved prompts. Instead of writing a detailed 300-word prompt every time, build it once as a skill and call it with a command. Output quality is also higher because skill instructions are more detailed than anything you'd type ad-hoc.

---

### Module 4 — Agentic Workflows

#### Sub-agents

**The mental model** — Sub-agents are like hiring employees. Each has its own brain (model), job description (the `.md` file), tools (permission level), and reports back to the main agent. Classic roles: research assistant, copywriter, QA engineer.

**Creating sub-agents** — Two methods: auto-generate with `/agents` (terminal only) or manually (create `.claude/agents/<agent-name>.md`). Manual structure:
- `name`: how you refer to the agent
- `description`: when Claude should use this agent — Claude reads this to route tasks
- `tools`: permission level (read-only / balanced / full)
- `model`: haiku/sonnet/opus
- `memory: project`: enables persistent memory across sessions

**Triggering** — Three methods: (1) natural language, (2) @mention (`@email-writer Can you make an email...`) — guaranteed to trigger, (3) session-wide (`//agent code-reviewer` — locks the session to one agent).

**Agent memory** — Sub-agents start from scratch each session. With `memory: project`, Claude creates `.claude/agent_memory/memory.md`. Loop: run task → Claude writes to memory → next session reads memory → output improves.

**Permission tiers:**
- Read-only: can look, can't touch. For research that shouldn't modify anything.
- Balanced: can read, edit, run commands, but cannot delete files. Safe for most work.
- Full access: omit the tools field entirely — inherits all tools.

**Sub-agent limitations** — Sub-agents cannot talk to each other. Results return to the parent agent only. They share the same context window as the main conversation.

#### Agent Teams

**When to use** — Agent teams solve the communication problem. Unlike sub-agents, each team member has its own context window and the agents can communicate with each other. Use when: building front end + back end + tests (interdependent), migrating multiple services simultaneously, any task where agents need to share intermediate outputs.

**Enabling** — Create `settings.json` in the project root with `{ "enableAgentTeams": true }`.

**Sales pipeline example** — 4-agent team for processing discovery call transcripts: (1) Insights Agent extracts company overview, pain points, timeline, red flags; (2) Proposal Builder reads the client summary; (3) CRM Agent creates structured JSON; (4) Follow-up Email Agent writes the follow-up. Agents 2 and 3 run in parallel once agent 1 completes; agent 4 runs after 2 and 3.

**Cost tradeoff** — Each agent in an agent team has its own context window — you're paying for multiple parallel Claude sessions. Michele's example: ~$80 for a complex build with agent teams vs much less with sub-agents. Rule: use sub-agents for most parallel work; use agent teams only when inter-agent communication is essential.

#### 8 Workflow Hacks

**Hack 1: Three-layer architecture** — Before building anything, drop a `CLAUDE.md` into the project with a three-layer folder structure. Layer 1 (Directives): SOPs and markdown files — objectives, inputs/outputs, tools, edge cases. Layer 2 (Orchestration): where the LLM logic lives — error handling, question routing, self-healing logic. Layer 3 (Execution): the actual code — Python scripts, API calls, data processing. This prevents the 0.9^5 = 59% accuracy problem.

**Hack 2: Skills** — Use skills from ai.tmpl.com to upgrade Claude's output quality.

**Hack 3: Spec → To-do → Build (milestone workflow)** — Never say "build me X." Instead: (1) ask Claude to write a `spec.md` with requirements, tech stack, and milestones; (2) ask Claude to generate a to-do list for milestone 1 only; (3) build milestone 1; (4) repeat for each subsequent milestone.

**Hack 4: Permission modes** — Bypass permissions (YOLO mode): Claude does everything without asking. Plan mode: collaborative planning before any execution. Rule: "a minute of planning saves 10 minutes of building."

**Hack 5: Sub-agents for parallel processing** — 84 emails → split across 4 sub-agents, all running simultaneously. For thousands of emails, this reduces hours to minutes.

**Hack 6: Context management** — `/compact` (compresses conversation, frees ~180k tokens), `/clear` (full reset), `/context` (shows token breakdown). Watch context usage before it degrades output quality.

**Hack 7: Pixel Agent extension** — VS Code extension that renders your Claude workspace as a visual game-like interface. Agents appear as characters in a room.

**Hack 8: Deployment** — Four options:

| Platform | Best for | Pricing |
|---|---|---|
| [[Modal]] | Easiest setup, Python-based, burst workflows | $30 free credits, pay-per-second |
| [[Railway]] | 24/7 continuous processes, GitHub-based | $1/month after 30-day trial |
| [[Render]] | Predictable flat billing, battle-tested | $7/month, no free tier |
| [[Replit]] | Code + deploy in browser, quick prototypes | Free tier (1 app) |

---

### Module 5 — Build

#### YouTube Content Pipeline

Michele's full production pipeline, rebuilt with Claude Code. Four stages:

**Stage 1: Ideation** — Three parallel agents:
- Comment scraper: fetches 1,369 comments from 5 competitor channels, exports to Google Sheets
- Competitor analysis: scores video ideas by estimated performance, exported to Sheets
- Twitter Monitor: scans 63 tweets → compiles findings → exports PDF → sends to email

**Stage 2: Packaging** — Two tasks:
- Thumbnail: face swap on a stock photo using file.ai nanobanana model
- Title generation: 300-title framework skill — generates hooks, A/B options, and emotional angle variants

**Stage 3: Video** — Two tools:
- 9-step script writing skill: intro hook, agenda, sections 1–5, CTA, outro
- Excalidraw diagram skill + visual skills for visual segments

**Stage 4: Post-video** — CTR tracking via Bitly link wrapping — measures clicks-to-views ratio per title to build an empirical title performance database.

#### Ferrari Landing Page Build

Live build from scratch — demonstrates the full plan→execute→review→deploy loop.

**Tools used:**
- Kid API for hero image: Imagen 2 model, $0.09/image
- Kling 3.0 for hero video: $0.625/5 seconds at Pro tier
- 21st.dev for UI components: copy-paste React/Tailwind components
- GitHub + [[Vercel]] for deployment: push repo → auto-deploys in ~2 minutes, live URL immediately

**The build loop:**
1. Drop `CLAUDE.md` with three-layer architecture
2. Plan mode: Claude proposes full structure, review before approving
3. Execute: Claude builds page using the plan + components + generated media
4. Review: check output, add revision comments in plan mode
5. Deploy: `git push` → Vercel picks it up → live in 2 minutes

The full build (planning → deployment) took under an hour with zero manual coding.
