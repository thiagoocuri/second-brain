---
title: "Hooks (Claude Code)"
type: concept
tags: [claude-code, automacao, eventos, configuracao, seguranca]
created: 2026-05-24
updated: 2026-05-24
sources: 1
---

## Definition

Hooks são ações automáticas que disparam em resposta a eventos específicos do Claude Code — independentemente do projeto ativo. Definidos em `settings.json` (nível global), aplicam-se a toda sessão. Permitem automatizar reações a ações do agente sem precisar instruir o Claude a cada vez.

Diferença de [[skills-ia]]: skills instruem *o Claude* sobre como fazer algo. Hooks disparam *scripts externos* automaticamente quando o Claude faz algo.

## Evidence & Examples

**4 tipos de evento** ([[michele-torti]], [[claude-code-masterclass]]):

| Evento | Quando dispara | Exemplo de uso |
|---|---|---|
| **Pre-tool use** | Antes de o Claude usar qualquer ferramenta | Bloquear acesso a arquivos `.env` |
| **Post-tool use** | Após uma ferramenta completar | Logar cada escrita de arquivo |
| **Stop/notification** | Quando o Claude termina uma tarefa | Enviar notificação desktop |
| **Post-tool use failure** | Quando uma chamada de ferramenta falha | Alertar por email sobre erros |

**Exemplos práticos:**

- **Notificação de conclusão**: hook de `stop` dispara `osascript` (macOS) ou `notify-send` (Linux) — você recebe um ping quando o Claude termina uma tarefa longa sem precisar ficar olhando a tela.
- **Proteção de `.env`**: hook de `pre-tool use` verifica o caminho do arquivo; se contiver `.env`, recusa a operação antes de o Claude ler ou escrever. Camada de segurança que não depende da instrução no [[claude-md]].
- **Audit log de compliance**: hook de `post-tool use` appends cada edição de arquivo em um log (`edits.log`) com timestamp — rastreabilidade total de tudo que o agente modificou.

**Caráter global:** hooks definidos em `settings.json` aplicam-se a **todos os projetos**, não apenas ao atual. É uma configuração de ambiente, não de projeto.

## Counter-evidence & Tensions

- Hooks mal configurados podem bloquear operações legítimas (ex: hook de `.env` muito amplo que bloqueia arquivos como `.env.example`). Testar hooks em ambiente isolado antes de aplicar globalmente.
- Hooks são scripts externos — erros neles não são reportados pelo Claude da mesma forma que erros de ferramenta. Debugging pode ser opaco.

## Related Concepts

[[claude-md]], [[agentes-ia]], [[skills-ia]], [[mcp]]

## Sources

[[claude-code-masterclass]]
