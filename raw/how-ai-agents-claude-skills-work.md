# How AI Agents & Claude Skills Work (Clearly Explained)

**Source:** NoteGPT Transcript — Podcast com Ross Mike  
**Format:** Transcrição de podcast (áudio → texto)  
**Tema:** Como agentes de IA e skills funcionam na prática

---

## Transcrição

**Host:** Ross, Mike, welcome back to the pod. By the end of this episode, what are people going to learn?

**Ross Mike:** I hope I'm going to share some wisdom on how you can use the agents better. There's a lot of information going on right now. I disagree with most of it and that's what we're going to talk about. So, at the end, whether you're building something, using an agent for some sort of work, you have the best output possible.

**Host:** And is this going to be a technical dive or a non-technical person can?

**Ross Mike:** Anyone can watch this. This is going to be a lot of diagrams. Easy. Basics. Let's go.

---

## Os modelos estão bons — o contexto é o que importa

**Ross Mike:** The first thing I want to announce — the models are good. The models are exceptionally good. Opus 4.6 is amazing. GPT 5.4 is amazing. Generally speaking, we've reached a point where the models are good. But context still matters and you have the power to steer the models in a direction where you can get quality or you can get slop.

Before we get into all that, we need to learn how context works. Context is the model assembling information that it needs to execute an action.

The way that context is assembled — in a coding agent, but really in any sort of agent — there's a general system prompt usually by the model provider. Claude Code leaked recently and one of the cool things I got to do is read the system prompt. They have this general system prompt that guides the model on how to act, what to do, what not to do.

---

## Agent.md / CLAUDE.md — 95% das pessoas não precisam

**Ross Mike:** A lot of people have agent.md files or claude.md files. 95% of people don't need this.

Imagine I told you every time we're about to shoot a podcast — "Greg, you need a microphone." You know you need a microphone. You've done this plenty of times.

If I'm building a website with Claude Code and I'm telling it "this codebase uses React" — I don't need to, because it has the codebase in context. It can check the code.

**Host:** So 95% of the time I don't even need to bother with an agent.md file?

**Ross Mike:** You don't. Unless it's some sort of proprietary information specific to your company or methodology that has to be referenced in every single conversation. The annoying part with an agent.md file is every time you go back and forth with the agent, it's added in the context.

If you have a thousand-line claude.md — that's like 7,000 tokens. You're spending 7,000 tokens on every run. Most likely not needed. It probably should be a skill.

---

## Skills — progressive disclosure

**Ross Mike:** The cool thing about skills — they're designed for what's called **progressive disclosure**.

When you have a skill file, the entire thing isn't added to context. It's just the title and the description.

So the agent has the title and description in context. When you say "create a notion report," it checks its context, sees the skill, and says "oh, I have this skill. Let me check out the entire document." The rest is only loaded when needed.

A skill basically looks like this:

```
name: [skill name]
description: [skill description]
---
[bunch of info]
```

What gets added into context is actually just the **name and the description**. The bunch of info doesn't get added — only when the agent realizes it needs this skill.

Two sentences versus an agent.md that has a thousand lines. Thousands of tokens compared to a couple hundred.

---

## Como criar skills do jeito certo

**Ross Mike:** Here's the thing — a lot of people will identify they have a workflow, and then jump to create the skill right away. This is the worst thing you can do.

Imagine you hire an employee or you're mentoring somebody — you're probably going to tell them what to do, let them try, help when they ask. There needs to be experiential learning.

The way I've been creating skills — I actually walk with it step by step on doing the workflow.

**Exemplo do canal do YouTube (análise de sponsors):**

I have an OpenClaw agent that has its own email. Every time I get an email from a sponsor, I forward it to the agent. The first time, I told it: "Check every 15 minutes. When you have an email, research the sponsor and tell me if they're worth it."

Every sponsor email I sent — it was like "legit, legit, legit, perfect." No rejection. No "this is bad" or "these guys are a scam." No deep research being done.

I realized: the model needs a step-by-step guide. This is when I create a skill. But I walked with it first:

- "Tell me about this company — their Twitter, YouTube, TrustPilot, if they've raised money. If two of these don't exist or aren't in good standing — automatic rejection."

Once we had a successful run and did it again and again — then I converted it to a skill.

**The updated workflow:**
1. Identify the workflow
2. Go back and forth and teach it — do each step manually
3. Once you've had a successful run, tell the AI: "Review what you did and create the skill"

Now it has actual context with how it worked. I don't handwrite skills. You can use AI to do it — but you should have the context of what a successful run looks like.

---

## Por que não baixar skills de outras pessoas

**Ross Mike:** I don't install skills. I've seen people — "oh, this Notion skill, this social media skill." I'll review it, check it out, even give it to my AI. But I don't download skills because your agent needs the context of a successful run, which you then turn into skills.

First of all, it's an easy way to attack somebody — be very careful with downloading random person's skills. Second, it's all about context. You want it to do the right thing. The only way it can do the right thing is if you give it the proper context.

---

## Construindo skills recursivamente

**Ross Mike:** Even though you have the skill.md, the agent at some point is still going to mess up — there are probably gaps. When it messes up, work with it again.

When it tells you "I failed, I couldn't do this task" — ask it: "Why did you fail? What's the error you got?" It will tell you descriptively. Then pass that failure back to the agent. Once it fixes it — **tell it to update the skill so this doesn't happen again.**

I have a report generator for my YouTube channel. It calls Notion, Dub Analytics, YouTube Analytics, Twitter Analytics — pulls from like eight data sources. There's no way you're going to one-prompt the agent and it'll do it. But every time I tell it to do that work, it takes 10 minutes and executes flawlessly. Why? I went through five loops — five iterations of recursively building this skill.

**The recursive skill loop:**
1. Build the skill from a successful run
2. Use it — it will mess up
3. Identify the error (ask the agent why it failed)
4. Pass the failure back — agent fixes it
5. Tell it to update the skill
6. Repeat

---

## Escalar para produtividade, não para o que parece legal

**Ross Mike:** I see a lot of people who, right off the rip, set up OpenClaw with 15 sub-agents, 30 skills — yet haven't even set up their own workflows.

I call it **scaling for productivity, not scaling for what looks cool.**

I started with one agent. This did everything — checked my spreadsheet, checked my sponsor email. Once I had predefined workflows, then I added a sub-agent. The sub-agent does all the marketing stuff. But I'm not creating it for the sake of creating it. It has skills, it has context, and it actually makes sense.

Now I have five sub-agents: one for marketing, one for business, one for personal. My system is more productive because I didn't scale for what looks cool. I scaled for productivity.

**Build up:**
- Start with one agent
- Build skills for your workflows
- Then add a sub-agent when you have enough to delegate
- Your main agent manages multiple sub-agents

---

## O contexto window — menos é mais

**Ross Mike:** If this is your context window, the optimal is between fresh and about 70%. The closer you get to 90–100%, it starts to get dumb. You want to save your context window — it saves you money, and it makes a more performant agent.

Less is more. Rely more on the model strengths. What the model needs is what's unique and special about you — your workflow, your business, not general knowledge.

Don't tell the model "use React." It knows React. Don't tell it things that should already be known. If you have something specific — a currency, a proprietary methodology — that's when you use agent.mds and claude.mds. But honestly, these are a force. You don't need them. **Skills, skills, skills** is what it's at.

---

## O que o modelo não tem que você tem

**Ross Mike:** The one thing you and I have that the models don't have is:
- My specific workflow
- My specific taste
- My specific strategy

Those can be codified in skills. This is why skills make sense when you build them — not if you download mine.

I have a code structure skill — 116 lines. When I tell the agent to clean up code structure, it checks its skills, sees the name and description (53 tokens), and progressively discloses the rest when it realizes it needs it. If this were in agent.md, that's 944 tokens every single time.

---

## Resumo final

**Ross Mike:** We've gotten to a point where the models are good. Context matters plus the harness. Less is more.

- Build up step by step
- Make it productive for you first before adding the shiny new thing
- Treat models like very new employees — not black magic boxes
- The models are really good at writing code (particularly TypeScript)
- Templates are going to have a renaissance — solid foundation = context for the agent

If you can't explain it in a few sentences, you probably don't really understand it.

---

*Transcrição adaptada de podcast. Participantes: Ross Mike (convidado) e Greg (host).*
