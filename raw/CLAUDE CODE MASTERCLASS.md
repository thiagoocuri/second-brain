---
created: 2026-05-24T00:00
updated: 2026-05-24T00:00
date: 2026-04-21
tags:
  - youtube
recording: https://www.youtube.com/watch?v=fQgJ7qXlyDE
views: 30099
creator: "[[Michele Torti]]"
people:
  - "[[Michele Torti]]"
duration: 13700
uploaded: 2026-04-21
transcript: "[[CLAUDE CODE MASTERCLASS 4 HOURS Build & Sell (2026) Transcript]]"
summary: Full Claude Code masterclass covering setup, customization, prompt engineering, agentic workflows, and building an AI automation business
categories:
  - "[[posts.base]]"
unread: true
---

> [!tldr]
> [[Michele Torti]] teaches five complete modules: Foundations (pricing, setup, [[CLAUDE.md]], models, context), Customization ([[Skills]], [[Hooks]], [[MCP]], commands), Prompt Engineering (5 session hacks), Agentic Workflows ([[Sub-agents]], [[Agent Teams]], 8 workflow hacks, deployment to [[Modal]]/[[Railway]]/[[Render]]/[[Replit]]), and Build (Michele's full YouTube content pipeline + Ferrari landing page from scratch). The central thesis: Claude Code is not just a coding assistant — it's an operating system for an entire AI business, and the skill ceiling is determined by how well you structure your inputs, memory, and agents.

## Module 1 — Foundations

**Pricing** — Three tiers. Free: limited usage, enough to test. Pro (~$17/month): recommended starting point. Max (~$100/month): for power users and production workflows. Cost scales with token usage across conversations.

**Hosting options** — Five ways to run Claude Code: [[VS Code]] extension, [[Cursor]] IDE, [[Antigravity]] IDE (VS Code fork), terminal (most visibility, shows all settings and flags), and the web app. Michele uses the terminal for agent work because it surfaces more context — model, tool use, permissions, memory state.

**Permissions** — Three categories Claude needs approval for: network access (hitting external APIs), browser control (interacting with the web), and file writes/reads. You set defaults in [[settings.json]] and override per session. Understand what each permission allows before granting it.

**[[CLAUDE.md]]** — The single most important file in any Claude Code project. Think of it as the brain: it holds everything Claude needs to know about the project so it doesn't have to ask. Generated with `/init` on first run. Exists at two levels: global (in `~/.claude/CLAUDE.md`, applies to all projects) and project-level (in the project root, overrides global). Five sections Michele recommends: project context, architecture, core workflows, design decisions, and important context (pitfalls, API quirks, naming conventions).

**The `.claude` directory** — Houses all Claude Code configuration: `CLAUDE.md`, `/commands` (slash command definitions), `/hooks` (trigger scripts), `/mcp.json` (MCP connections), `settings.json` (permissions and model preferences), `/skills` (instruction manuals), `/agents` (sub-agent definitions), `/agent_memory` (persistent agent memory).

**Setup Mode vs Use Mode** — Two distinct phases. Setup Mode: scaffold the project, write CLAUDE.md, install skills, configure MCPs, create sub-agents. Use Mode: actually build and run tasks. Most people jump straight to Use Mode without Setup, and then wonder why Claude is inconsistent. Setup is the multiplier.

**How Claude works** — Four-step loop: understand (read your message + context files) → plan (decide what to do and which tools to use) → use tools (read/write files, run commands, call APIs) → output (return results). The quality of your output is determined at the "understand" step, which is why CLAUDE.md and skills matter so much.

**Models** — Three options, each with a different cost/capability profile:
- **[[Claude Haiku]]**: cheapest, fastest. For simple lookups, file reading, quick transformations.
- **[[Claude Sonnet]]**: default, balanced. Good for code, writing, most daily tasks. Start here.
- **[[Claude Opus]]**: most powerful, most expensive. For hard debugging, complex full-stack builds, anything requiring deep reasoning. Use only when Sonnet fails.

**Context window** — 200,000 tokens per conversation. Every message you send, every response Claude gives, every file it reads, every tool call it makes fills this window. When full, performance degrades. Michele's rule: treat it like a notebook with 200k pages. Don't fill it with trash — start fresh for unrelated tasks.

**Output types** — Text, Markdown (documents, reports), code (files, scripts), and artifacts (interactive HTML/JS widgets previewed in browser). Knowing which output type you want helps you prompt more precisely.

**Slash commands** — `/init` (generate CLAUDE.md), `/clear` (reset conversation context), `/compact` (summarize context while preserving state), `/context` (show token usage breakdown), `/mcp` (manage MCP servers), `/doctor` (check Claude Code health), `/resume` (continue previous session), `/review` (code review), `/config` (settings).

**Interactive vs headless mode** — Interactive: you're in the loop, Claude asks approval before destructive actions. Headless: Claude runs autonomously without prompts — used for scheduled automation and CI/CD pipelines.

## Module 2 — Customization

**[[Skills]]** — Instruction manuals that Claude reads before performing a task. Stored in `.claude/skills/`. Each skill is a folder containing `skill.md` (required — the actual instructions) plus optional `references/` (supporting docs) and `scripts/` (helper scripts Claude can run). Without a skill, Claude guesses and gives inconsistent output. With a skill, it follows a pattern every time. Find skills at [[ai.tmpl.com]] — 683+ skills and growing. Top picks: Canva Design (presentations), PDF skill (read/extract/fill/merge/split), website builder, senior backend architect.

**Installing skills** — Paste the skill URL or code into Claude Code and say "Install this skill." Claude handles the rest — creates the folder, writes the files. To build manually: create `.claude/skills/<skill-name>/skill.md` with your instructions. Michele built a YouTube title generator skill live to demonstrate the pattern — input a topic, output 10 titles with hooks, store in an output file.

**[[Skill Creator]]** — Official [[Anthropic]] meta-skill. Describe what you want in plain English, it generates a complete skill file in ~5 minutes. Access via `/manage plugins`. Use this when you can't find an existing skill that fits.

**Skill evaluation** — `eval.json` defines what good output looks like. `trigger-eval.json` contains 20 test prompts that trigger the skill. Run evaluations to benchmark before/after changes — the skill improves itself based on the gap. This is the self-improving loop that makes skills better over time.

**Commands** — Slash command shortcuts that call skills. Stored in `.claude/commands/`. Create a file named `command-name.md` with a description and the skill it should trigger. Now `/command-name` runs the skill without typing instructions. Michele's example: `/ideas` triggers a content ideas skill that outputs a PDF.

**[[Hooks]]** — Automatic actions that fire on events, regardless of what project you're in. Defined in `settings.json`. Four event types:
1. **Pre-tool use**: runs before Claude uses a tool (e.g., block access to `.env` files)
2. **Post-tool use**: runs after a tool completes (e.g., log every file write)
3. **Stop/notification**: fires when Claude finishes a task (e.g., send a desktop notification)
4. **Post-tool use failure**: fires when a tool call fails (e.g., alert on errors)
Hook examples: notification hook (ping you when Claude finishes a long task), `.env` protection hook (refuse any read/write to `.env`), audit log hook (append every file edit to a log for compliance). Hooks are global — they apply to every project.

**[[MCP]]** (Model Context Protocol) — Plugins that give Claude new abilities beyond its built-in tools. Configured in `.mcp.json`. Two recommended MCPs:
- **[[Chrome DevTools MCP]]**: full browser control — click, fill forms, navigate, take screenshots. Essential for web automation and visual testing.
- **[[Supabase MCP]]**: vector database connection. Enables semantic search, persistent data, RAG patterns.
Find more at [[mcp-servers.org]]. Token cost warning: loading two MCPs costs ~10,800 tokens of context automatically. Recommendation: use 2–3 MCPs maximum, and convert stable MCPs into skills when possible to save context.

## Module 3 — Prompt Engineering

**Hack 1: Split prompts** — One task per conversation. Don't chain "research X, then write Y, then format Z" in a single prompt. Give Claude one clear task, review the output, then give the next. Chaining compounds errors — each step at 90% accuracy means a 5-step chain is only 59% accurate. Breaking tasks into separate prompts resets the error rate at each step.

**Hack 2: Plan mode** — For any complex multi-step task, start in plan mode (Shift+Tab toggle). Claude maps out the full plan before writing a single line of code. Review the plan, add comments to refine it, then approve execution. The same way an architect draws blueprints before building — don't let Claude start building until the plan is right.

**Hack 3: Kitchen sink vs clean session** — Every file Claude reads, every message exchanged, eats context. Two scenarios: "kitchen sink" (one long session with all project context loaded — useful when everything is related) vs "clean session" (fresh conversation for each unrelated task — 9% context vs 42% context on the same work). Check current usage with `/context`. Rule: start a new conversation when switching to an unrelated task.

**Hack 4: CLAUDE.md as permanent memory** — Every rule you'd otherwise type in every session belongs in CLAUDE.md. Once it's there, Claude always knows it. Michele's example: instead of typing "always respond in Portuguese, keep responses under 150 words, never use em dashes" every conversation, encode it once in CLAUDE.md and it applies forever.

**Hack 5: Skills as reusable prompts** — Skills are saved prompts. Instead of writing a detailed 300-word prompt every time you want an [[Excalidraw]] diagram or a content ideas PDF, build it once as a skill and call it with `/diagram` or `/ideas`. The output quality is also higher because the skill instructions are more detailed than anything you'd type ad-hoc.

## Module 4 — Agentic Workflows

### Sub-agents

**The mental model** — Right now, Claude Code is a one-person business doing everything: research, write, test, organize. Sub-agents are like hiring employees. Each has its own brain (model), its own job description (the `.md` file), its own tools (permission level), and each reports back to the main agent. Classic roles: research assistant, copywriter, QA engineer.

**Creating sub-agents** — Two methods: auto-generate with `/agents` (terminal only, walks through name/description/model/tools/color/memory interactively) or manually (create `.claude/agents/<agent-name>.md`). Manual structure:
- `name`: how you refer to the agent
- `description`: when Claude should use this agent — Claude reads this to route tasks
- `tools`: permission level (read-only = read/grep/glob; balanced = read/edit/bash/grep/glob; full = empty, inherits everything)
- `model`: haiku/sonnet/opus
- `memory: project`: enables persistent memory across sessions
- Instructions block: the actual personality and step-by-step rules

**Triggering** — Three methods: (1) natural language ("can you use the code reviewer to check my changes"), (2) @mention (`@email-writer Can you make an email to Jessica...`) — guaranteed to trigger because it references the agent directly, (3) session-wide (`//agent code-reviewer` — locks the session to one agent). Recommendation: start with natural language, move to @mention when you have multiple overlapping agents.

**Agent memory** — Sub-agents start from scratch each session — no memory of previous conversations. Solution: add `memory: project` to the agent definition. Claude creates `.claude/agent_memory/memory.md` and writes feedback/tone/preferences there. On each new session, the agent reads its memory first. The loop: run task → Claude writes to memory → next session reads memory → output improves. Self-improving sub-agents.

**Permission tiers:**
- Read-only: can look, can't touch. For research that shouldn't modify anything.
- Balanced: can read, edit, run commands, but cannot delete files. Safe for most work.
- Full access: omit the tools field entirely — inherits all tools. Only use for well-defined, structured, low-risk tasks.

**Sub-agent limitations** — Sub-agents cannot talk to each other. Results return to the parent agent only. They share the same context window as the main conversation. This means: great for independent parallel tasks (write LinkedIn post + blog post simultaneously), but problematic when tasks depend on each other's output (blog post tone needs to match LinkedIn tone — they can't coordinate).

### Agent Teams

**When to use** — Agent teams solve the communication problem. Unlike sub-agents, each team member has its own context window and the agents can communicate with each other. Use when: building front end + back end + tests (they're interdependent), migrating multiple services simultaneously, any task where agents need to share intermediate outputs.

**Structure** — One team lead receives the task and spawns the team. Each teammate has its own context, shared task list, and can talk to other teammates. Think of it as an actual company with departments that can email each other.

**Enabling** — Create `settings.json` in the project root with `{ "enableAgentTeams": true }`. Then prompt Claude to create the team structure.

**Sales pipeline example** — A 4-agent team for processing discovery call transcripts: (1) Insights Agent extracts company overview, pain points, timeline, red flags → outputs `client-summary.md`; (2) Proposal Builder reads the client summary → outputs `product-proposal.md`; (3) CRM Agent creates structured JSON for CRM update; (4) Follow-up Email Agent writes the follow-up. Agent 1 runs first; agents 2 and 3 run in parallel once agent 1 completes; agent 4 runs after agents 2 and 3.

**Parallelization advantage** — Traditional: 6 tasks × 1 minute each = 6 minutes. Agent team with 3 workers: 6 tasks ÷ 3 workers = 2 minutes. For complex workflows, this can reduce hours to minutes.

**Cost tradeoff** — Each agent in an agent team has its own context window, meaning you're paying for multiple parallel Claude sessions. Michele's example: running a 4-agent team consumed tokens at a frightening rate. Estimated: ~$80 for a complex build with agent teams vs much less with sub-agents. Rule: use sub-agents for most parallel work; use agent teams only when inter-agent communication is essential.

### 8 Workflow Hacks

**Hack 1: Three-layer architecture** — Before building anything, drop a `CLAUDE.md` into the project with a three-layer folder structure. Layer 1 (Directives): SOPs and markdown files that tell Claude what to do — objectives, inputs/outputs, tools, edge cases. Layer 2 (Orchestration): where the LLM logic lives — error handling, question routing, self-healing logic. Layer 3 (Execution): the actual code — Python scripts, API calls, data processing. This prevents the 0.9^5 = 59% accuracy problem: with structure, Claude knows where to put things and recovers from errors predictably.

**Hack 2: Skills** — Use skills from [[ai.tmpl.com]] to upgrade Claude's output quality. Before vs after example: Canva Design skill dramatically improved presentation formatting, colors, and layout compared to Claude's default output.

**Hack 3: Spec → To-do → Build (milestone workflow)** — Never say "build me X." Instead: (1) ask Claude to write a `spec.md` with requirements, tech stack, and milestones; (2) ask Claude to generate a to-do list for milestone 1 only; (3) build milestone 1; (4) repeat for each subsequent milestone. More time upfront, 10× better output. The spec lives in `directives/` per the three-layer architecture.

**Hack 4: Permission modes** — Bypass permissions (YOLO mode): Claude does everything without asking. Best for simple, well-defined tasks. Plan mode: collaborative planning before any execution. Rule: "a minute of planning saves 10 minutes of building." Toggle with Shift+Tab.

**Hack 5: Sub-agents for parallel processing** — Email classifier example: 84 emails → split across 4 sub-agents (1–20, 21–40, 41–60, 61–84), all running simultaneously. For thousands of emails, this reduces hours to minutes. Split any batch task across agents when the items are independent.

**Hack 6: Context management** — Three tools: `/compact` (compresses conversation to a summary, frees ~180k tokens while preserving project state — use when the chat gets too long but you want to keep working), `/clear` (full reset, starts fresh), `/context` (shows token breakdown: system prompt, tools, memory, skills, messages, free space). Watch context usage before it degrades output quality.

**Hack 7: Pixel Agent extension** — VS Code extension that renders your Claude workspace as a visual game-like interface. Agents appear as characters in a room; red indicator shows when an agent needs approval. Makes multi-agent work tangible for visual thinkers. Install via VS Code extensions search "Pixel Agents." Access via Command Palette → "Pixel Agent Show Panel."

**Hack 8: Deployment** — Four options to take an agent workflow off your local machine and run it 24/7:

| Platform | Best for | Pricing |
|---|---|---|
| [[Modal]] | Easiest setup, Python-based, burst workflows | $30 free credits, pay-per-second |
| [[Railway]] | 24/7 continuous processes, GitHub-based | $1/month after 30-day trial |
| [[Render]] | Predictable flat billing, battle-tested | $7/month, no free tier |
| [[Replit]] | Code + deploy in browser, quick prototypes | Free tier (1 app) |

Deployment flow: tell Claude "host this in Modal, run every Monday 9am London time" → Claude creates `modal_app.py` → pushes to Modal → done. Debugging flow (same for all platforms): workflow breaks → open platform logs → find red error → copy error → paste into Claude Code → Claude fixes → redeploy. AWS/GCP/Azure exist but are enterprise-grade overkill for most workflows.

## Module 5 — Build

### YouTube Content Pipeline

Michele's full production pipeline, rebuilt with Claude Code. Four stages:

**Stage 1: Ideation** — Three parallel agents:
- Comment scraper: fetches 1,369 comments from 5 competitor channels ([[Nate O'Brien]], [[Liam O'Malley]], and others), exports to Google Sheets
- Competitor analysis: [[Alora]] multiple scoring — scores video ideas by estimated performance, exported to Sheets
- Twitter Monitor: scans 63 tweets → compiles findings → exports PDF → sends to email

**Stage 2: Packaging** — Two tasks:
- Thumbnail: face swap on a stock photo using [[file.ai]] nanobanana model
- Title generation: 300-title framework skill — generates hooks, A/B options, and emotional angle variants

**Stage 3: Video** — Two tools:
- 9-step script writing skill: intro hook, agenda, section 1–5, CTA, outro — structured output for every video
- [[Excalidraw]] diagram skill + visual skills: generates diagrams for visual segments mid-production

**Stage 4: Post-video** — CTR tracking via [[Bitly]] link wrapping — measures clicks-to-views ratio per title to build an empirical title performance database over time.

### Ferrari Landing Page Build

Live build from scratch — demonstrates the full plan→execute→review→deploy loop.

**Tools used:**
- [[Kid API]] for hero image: [[Imagen 2]] model, $0.09/image, generates photorealistic product shots
- [[Kling 3.0]] for hero video: $0.625/5 seconds at Pro tier, motion video from a still
- [[21st.dev]] for UI components: copy-paste React/Tailwind components, no design from scratch
- [[GitHub]] + [[Vercel]] for deployment: push repo → Vercel auto-deploys in ~2 minutes, live URL immediately

**The build loop:**
1. Drop `CLAUDE.md` with three-layer architecture
2. Plan mode: Claude proposes full structure, review before approving
3. Execute: Claude builds page using the plan + 21st.dev components + generated media
4. Review: check output, add revision comments in plan mode
5. Deploy: `git push` → Vercel picks it up → live in 2 minutes

The full build (planning → deployment) took under an hour with zero manual coding.

**Business context** — Michele runs a 6-figure AI automation agency, has taught 10,000+ people, and offers a 90-day 1-on-1 mentorship program for people building AI automation businesses from scratch. The masterclass is designed to take a complete beginner from setup to deployable, sellable agent workflows.
