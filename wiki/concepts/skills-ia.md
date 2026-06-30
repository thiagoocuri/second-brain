---
title: "Skills de IA"
type: concept
tags: [ai, skills, claude-code, contexto, produtividade]
created: 2026-04-18
updated: 2026-05-24
sources: 2
---

## Definition

Skills são arquivos markdown que codificam workflows específicos para [[agentes-ia]]. Diferente de um CLAUDE.md que é carregado em todo turno, skills usam **progressive disclosure**: apenas o nome e a descrição entram no contexto do agente (~53 tokens). O conteúdo completo só é carregado quando o agente identifica que precisa daquela skill para executar a tarefa atual.

Estrutura mínima de uma skill:

```
---
name: nome-da-skill
description: quando e para que usar esta skill
---

[instruções passo a passo do workflow]
```

## Evidence & Examples

**Custo de tokens comparado** (Ross Mike, [[claude-code-masterclass]]):
- Skill com 116 linhas como agent.md: **944 tokens por turno**
- Mesma skill como arquivo de skill: **53 tokens por turno** (só nome + descrição)
- Economia: ~94% dos tokens, mantendo a funcionalidade completa

**Como construir skills corretamente:**

1. **Não crie o arquivo direto.** A maioria das pessoas vai ao ChatGPT, descreve o workflow e pede para gerar o SKILL.md. Resultado: o agente não tem contexto de uma execução bem-sucedida.
2. **Execute o workflow manualmente com o agente.** Passo a passo, turno a turno — "agora faz isso, agora verifica aquilo." Identifique onde ele erra e corrija na hora.
3. **Após uma execução completa bem-sucedida**, diga: *"Revise o que você fez e crie o arquivo de skill."* Agora ele tem contexto real para escrever boas instruções.
4. **Recursive skill building:** quando a skill falhar em produção, não se frustre. Identifique o erro ("por que você falhou? qual foi o erro?"), corrija, e mande o agente **atualizar o próprio arquivo de skill**. Repita até estabilizar (~3–5 iterações).

**Quando NÃO usar skills:**
- Tarefas genéricas que o modelo já sabe fazer (usar React, escrever em inglês, formatar datas)
- Conhecimento que já está no código/arquivos do projeto

**Quando usar skills:**
- Workflow proprietário com sequência de passos não-óbvios
- Integrações com APIs específicas que o agente tende a errar
- Formato ou estilo muito específico do usuário (ex: estrutura de relatório, critérios de qualificação de leads)

**Estrutura de pasta de uma skill** ([[michele-torti]], [[claude-code-masterclass]]):
```
.claude/skills/<nome-da-skill>/
├── skill.md          ← obrigatório: as instruções
├── references/       ← docs de suporte (opcional)
└── scripts/          ← scripts que o Claude pode executar (opcional)
```

**Skill Creator** ([[claude-code-masterclass]]): meta-skill oficial da Anthropic. Descreva em português o que você quer, ela gera o arquivo de skill completo em ~5 minutos. Acessada via `/manage plugins`. Alternativa ao processo manual quando não há skill existente que se encaixe.

**Sistema de avaliação de skills** ([[claude-code-masterclass]]):
- `eval.json`: define o que é um bom output para esta skill
- `trigger-eval.json`: 20 prompts de teste que acionam a skill
- Rodar avaliações compara antes/após mudanças — a skill se auto-aprimora com base no gap. Loop de melhoria contínua análogo ao processo de recursive skill building do Ross Mike.

**Commands como atalhos de skill** ([[claude-code-masterclass]]): criar `.claude/commands/<nome>.md` com descrição e a skill que deve acionar. Agora `/nome` roda a skill sem digitar instruções. Exemplo: `/ideias` aciona skill de geração de conteúdo que outputa PDF.

**Onde encontrar skills:** ai.tmpl.com — 683+ skills por categoria (Canva Design, PDF, website builder, senior backend architect, etc.). Tensão com recomendação de Ross Mike de não usar skills de terceiros — ver Counter-evidence.

## Counter-evidence & Tensions

- [[claude-code-masterclass]]: Ross Mike é contra baixar skills de terceiros por dois motivos: (1) risco de segurança — skills são um vetor de ataque fácil; (2) o agente não tem contexto da execução bem-sucedida do criador original, então a skill pode falhar de formas inesperadas. [[claude-code-masterclass]] (Torti) recomenda ativamente o catálogo — tensão não resolvida.
- Skills muito longas ou mal estruturadas podem ser piores que um [[claude-md]] simples — o benefício de progressive disclosure depende de a skill ser modular e autocontida.

## Related Concepts

[[agentes-ia]], [[context-window]], [[progressive-disclosure]], [[sub-agentes]], [[claude-md]], [[mcp]]

## Sources

[[claude-code-masterclass]]
