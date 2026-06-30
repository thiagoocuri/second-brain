# Commands

---

## Second Brain Wiki

> Operações do sistema de wiki pessoal. Estrutura: `raw/` (você escreve) → `wiki/` (LLM mantém).

| Comando / Frase | O que dispara | O que o agente faz |
|---|---|---|
| `"ingest [arquivo]"` / `"process [arquivo]"` | **INGEST** | Lê o arquivo em `raw/`, discute takeaways, cria página em `wiki/sources/`, atualiza entidades, conceitos, `overview.md`, `index.md` e `log.md` |
| Qualquer pergunta sobre o conteúdo do wiki | **QUERY** | Lê `index.md`, busca páginas relevantes, responde com citações. Oferece salvar como análise em `wiki/` |
| `"lint the wiki"` / `"health check"` / `"audit"` | **LINT** | Verifica contradições, páginas órfãs, conceitos sem página, claims desatualizados e gaps de conteúdo. Gera relatório markdown |
| Início de sessão (automático) | **SESSION START** | Lê CLAUDE.md + `index.md` + últimas 10 entradas do `log.md`. Resume estado atual do wiki |

---

## Superpowers / Conteúdo

| Comando | O que faz | Quando usar |
|---|---|---|
| `/summarize` | Sumariza URL, artigo, PDF ou vídeo e cria nota Obsidian rica com wikilinks | Ingesta rápida de qualquer conteúdo externo |
| `/summarize-call` | Transcreve gravação de reunião/chamada com diarização e cria nota no vault | Reuniões, entrevistas, podcasts com áudio/vídeo local |
| `/brainstorming` | Explora intenção e alternativas antes de qualquer tarefa criativa ou analítica | Antes de criar estratégia, análise ou ingestão complexa |

---

## Superpowers / Automação & Config

| Comando | O que faz | Quando usar |
|---|---|---|
| `/schedule` | Cria agente remoto com agendamento cron | Lint semanal do wiki, revisões periódicas |
| `/loop` | Repete um comando num intervalo de tempo | Monitorar uma tarefa em andamento |
| `/update-config` | Edita `settings.json` para comportamentos automatizados e permissões | "Sempre que X, faça Y" — hooks e permissões |
| `/keybindings-help` | Customiza atalhos de teclado do Claude Code | Rebindear teclas, criar chord shortcuts |
| `/fewer-permission-prompts` | Analisa histórico e adiciona allowlist para reduzir prompts de permissão | Quando os prompts de permissão estão irritando |
| `/init` | Inicializa configuração do projeto no Claude Code | Setup inicial de um projeto novo |

---

## Marketing Skills

> **Como usar:** Invoque diretamente (`/cro`, `/emails`, `/seo-audit`) ou descreva a tarefa em linguagem natural — o agente escolhe a skill certa.
> Toda skill lê `product-marketing` primeiro para entender seu produto/audiência. Configure esse arquivo antes de começar.

---

## Triviais

| Comando | O que faz | Quando usar |
|---|---|---|
| `/product-marketing` | Cria/atualiza o contexto central do produto (público, posicionamento, diferenciais) | Antes de qualquer outra coisa |
| `/customer-research` | Conduz, analisa e sintetiza pesquisa com clientes | Antes de escrever copy ou planejar campanha |
| `/marketing-ideas` | Gera 140+ ideias de marketing para SaaS | Quando travar em estratégia |
| `/marketing-psychology` | Aplica princípios de psicologia comportamental ao marketing | Para aumentar persuasão em qualquer peça |

---

## Conversão (CRO)

| Comando | O que faz | Quando usar |
|---|---|---|
| `/cro` | Otimiza páginas e formulários para conversão | Qualquer página com baixa conversão |
| `/signup` | Otimiza fluxo de cadastro e ativação de trial | Taxa de signup baixa |
| `/onboarding` | Melhora ativação pós-signup e time-to-value | Usuários não chegam ao "aha moment" |
| `/popups` | Cria/otimiza popups, modais e banners | Captura de leads, anúncios in-page |
| `/paywalls` | Cria/otimiza telas de upgrade e upsell | Conversão free → pago |

---

## Copy & Conteúdo

| Comando | O que faz | Quando usar |
|---|---|---|
| `/copywriting` | Escreve copy para homepage, landing pages, qualquer página | Do zero |
| `/copy-editing` | Edita e melhora copy existente | Refinar textos já escritos |
| `/cold-email` | Escreve emails B2B de prospecção e sequências de follow-up | Outreach |
| `/emails` | Cria sequências de email automatizadas e fluxos de lifecycle | Welcome, nurture, re-engajamento |
| `/social` | Cria conteúdo para LinkedIn, Twitter/X, Instagram, TikTok | Posts e estratégia de redes sociais |
| `/video` | Produz scripts e conteúdo de vídeo com IA | YouTube, Reels, demos |
| `/image` | Cria e otimiza imagens de marketing com IA | Banners, thumbnails, social |
| `/content-strategy` | Planeja estratégia de conteúdo e decide tópicos | Antes de começar a produzir conteúdo |

---

## SEO & Descoberta

| Comando                  | O que faz                                                                 | Quando usar                            |
| ------------------------ | ------------------------------------------------------------------------- | -------------------------------------- |
| `/seo-audit`             | Audita e diagnostica problemas técnicos e on-page de SEO                  | Diagnóstico geral do site              |
| `/ai-seo`                | Otimiza para aparecer em respostas de IA (ChatGPT, Perplexity, Google AI) | AEO / GEO / LLMO                       |
| `/programmatic-seo`      | Gera páginas SEO em escala com templates e dados                          | Criar centenas de páginas              |
| `/site-architecture`     | Planeja hierarquia, navegação e estrutura de URLs                         | Redesign ou novo site                  |
| `/schema`                | Adiciona e otimiza structured data / schema markup                        | Rich snippets, visibilidade em busca   |
| `/competitors`           | Cria páginas de comparação e alternativas para SEO                        | "vs. Concorrente", "alternativas ao X" |
| `/competitor-profiling`  | Pesquisa e perfila concorrentes a partir das URLs deles                   | Análise competitiva profunda           |
| `/aso`                   | Audita e otimiza listagem na App Store e Google Play                      | Apps móveis                            |
| `/directory-submissions` | Submete produto em diretórios de startups, SaaS e IA                      | Link building e descoberta             |

---

## Anúncios Pagos

| Comando | O que faz | Quando usar |
|---|---|---|
| `/ads` | Planeja e gerencia campanhas no Google, Meta, LinkedIn, Twitter | Campanhas de tráfego pago |
| `/ad-creative` | Gera e itera em criatives (headlines, textos, descrições) em escala | Precisar de muitas variações de anúncio |
| `/ab-testing` | Planeja e implementa testes A/B e programas de experimentação | Otimizar qualquer elemento com dados |

---

## Analytics & Medição

| Comando | O que faz | Quando usar |
|---|---|---|
| `/analytics` | Configura, audita e melhora tracking de eventos | GA4, Mixpanel, Amplitude, etc. |

---

## Retenção & Crescimento

| Comando | O que faz | Quando usar |
|---|---|---|
| `/churn-prevention` | Cria fluxos de cancelamento, ofertas de retenção e dunning | Churn alto ou recuperação de pagamentos |
| `/referrals` | Cria e otimiza programas de referral e afiliados | Crescimento por indicação |
| `/free-tools` | Planeja e constrói ferramentas gratuitas para geração de leads e SEO | Lead magnets técnicos |
| `/lead-magnets` | Cria e otimiza lead magnets para captura de email | Construir lista |
| `/community-marketing` | Constrói e usa comunidades online para crescimento | Discord, Slack, fóruns |
| `/co-marketing` | Encontra parceiros e planeja campanhas conjuntas | Parcerias e co-promoções |

---

## Estratégia & Monetização

| Comando | O que faz | Quando usar |
|---|---|---|
| `/launch` | Planeja lançamento de produto ou feature | Product Hunt, Beta, GA |
| `/pricing` | Define estratégia de pricing, pacotes e monetização | Revisão de preços |

---

## Vendas & RevOps

| Comando | O que faz | Quando usar |
|---|---|---|
| `/revops` | Gerencia lifecycle de leads, scoring, routing e pipeline | Marketing → Vendas |
| `/sales-enablement` | Cria decks, one-pagers, scripts de demo e docs de objeções | Materiais para o time de vendas |

---

## Superpowers / Desenvolvimento

| Comando | O que faz | Quando usar |
|---|---|---|
| `/systematic-debugging` | Investiga bugs de forma estruturada e sistemática | Quando o bug não é óbvio |
| `/test-driven-development` | Guia desenvolvimento com ciclo red-green-refactor | Ao escrever nova funcionalidade com testes |
| `/writing-plans` | Cria plano de implementação antes de tocar código | Antes de qualquer tarefa multi-step |
| `/executing-plans` | Executa planos de implementação com tasks | Ao implementar um plano aprovado |
| `/verification-before-completion` | Verifica que a mudança funciona antes de reportar como feita | Antes de declarar uma tarefa completa |
| `/requesting-code-review` | Prepara e solicita code review do diff atual | Antes de mergear |
| `/receiving-code-review` | Processa feedback de code review e aplica correções | Ao receber review de um PR |
| `/finishing-a-development-branch` | Finaliza uma branch: testa, revisa, prepara PR | Antes de abrir um PR |
| `/subagent-driven-development` | Executa planos com tarefas independentes em paralelo via subagents | Implementações grandes com tasks independentes |
| `/dispatching-parallel-agents` | Despacha múltiplos agentes em paralelo para tarefas independentes | Pesquisas ou implementações paralelizáveis |
| `/using-git-worktrees` | Usa git worktrees para isolar trabalho em paralelo | Múltiplas features ou fixes simultâneos |
| `/writing-skills` | Cria novas skills/plugins para o vault | Automatizar comportamentos personalizados |

---

## Código & Qualidade

| Comando | O que faz | Quando usar |
|---|---|---|
| `/code-review` | Revisa diff em busca de bugs, simplificações e melhorias (níveis: low/medium/high/ultra) | Antes de mergear qualquer mudança |
| `/simplify` | Revisa código alterado e aplica simplificações, reuso e eficiência | Após implementar — limpar sem mudar comportamento |
| `/verify` | Roda o app e observa o comportamento real de uma mudança | Confirmar que uma feature funciona de verdade |
| `/run` | Inicia o app do projeto e observa o estado atual | Ver o app rodando, confirmar setup |
| `/security-review` | Revisa código em busca de vulnerabilidades de segurança | Antes de expor endpoints, autenticação, dados |
| `/review` | Review geral do estado do repositório e branch | Visão geral do que foi feito |

---

## Design & Frontend

| Comando | O que faz | Quando usar |
|---|---|---|
| `/frontend-design` | Implementa interfaces seguindo boas práticas de design e UX | Criar ou melhorar telas e componentes |
| `/design-consultation` | Consulta de design — avalia abordagem e alternativas antes de implementar | Antes de começar um novo componente ou tela |
| `/design-html` | Cria protótipos HTML/CSS de alta fidelidade | Prototipagem rápida de UI |
| `/design-review` | Revisa implementação de UI contra o design original | Garantir fidelidade ao design |
| `/design-shotgun` | Gera múltiplas variações de design rapidamente | Explorar opções visuais |

---

## Documentos

| Comando | O que faz | Quando usar |
|---|---|---|
| `/pdf` | Lê, processa e extrai conteúdo de arquivos PDF | Ingerir PDFs no wiki |
| `/docx` | Lê e processa documentos Word (.docx) | Ingerir documentos Word |
| `/xlsx` | Lê e processa planilhas Excel (.xlsx) | Analisar dados em planilha |
| `/pptx` | Lê e processa apresentações PowerPoint (.pptx) | Ingerir apresentações |
| `/document-generate` | Gera documentos formais a partir de contexto | Criar relatórios, specs, docs |
| `/document-release` | Gera release notes e documentação de versão | Ao lançar uma versão |
| `/make-pdf` | Converte conteúdo em arquivo PDF | Exportar nota ou análise como PDF |

---

## iOS

| Comando | O que faz | Quando usar |
|---|---|---|
| `/ios-fix` | Diagnostica e corrige bugs em projetos iOS/Swift | Bugs em app iOS |
| `/ios-qa` | Testa e valida funcionalidades em app iOS | QA antes de release |
| `/ios-design-review` | Revisa UI/UX de app iOS contra design | Garantir fidelidade no app |
| `/ios-sync` | Sincroniza estado e contexto de projeto iOS | Atualizar entendimento do projeto |
| `/ios-clean` | Limpa build caches e artifacts do Xcode | Problemas de build |

---

## SEO Especializado

| Comando | O que faz | Quando usar |
|---|---|---|
| `/seo` | Ponto de entrada geral para fluxos de SEO | Diagnóstico inicial |
| `/seo-plan` | Cria plano estratégico de SEO priorizado | Montar roadmap de SEO |
| `/seo-page` | Otimiza uma página específica on-page | Melhorar ranking de página individual |
| `/seo-content` | Avalia qualidade de conteúdo: E-E-A-T, legibilidade, profundidade | Auditar artigos e páginas |
| `/seo-content-brief` | Cria brief de conteúdo baseado em SERP e intenção | Antes de escrever um artigo |
| `/seo-technical` | Analisa crawlability, indexação, mobile e Core Web Vitals | Problemas técnicos de SEO |
| `/seo-backlinks` | Analisa perfil de backlinks via Moz, Bing e Common Crawl | Link building e autoridade |
| `/seo-cluster` | Cria clusters semânticos e arquitetura hub-and-spoke | Estratégia de tópicos |
| `/seo-local` | Otimiza SEO local: GBP, NAP, citations, reviews | Negócios locais |
| `/seo-ecommerce` | Valida schema de produto, Google Shopping e Amazon | E-commerce |
| `/seo-geo` | Otimiza para IA search: llms.txt, citabilidade, GEO | Google AI, ChatGPT, Perplexity |
| `/seo-google` | Busca dados via CrUX, GSC e GA4 | Dados reais de performance |
| `/seo-dataforseo` | Busca dados via DataForSEO: SERP, keywords, backlinks | Análise com dados ao vivo |
| `/seo-sxo` | Analisa intenção e experiência de busca (SXO) | Quando conteúdo bom não ranqueia |
| `/seo-competitor-pages` | Analisa páginas de concorrentes para SEO | Benchmarking competitivo |
| `/seo-hreflang` | Valida e corrige tags hreflang para SEO internacional | Sites multilíngues |
| `/seo-images` | Audita e otimiza imagens para SEO | Alt texts, lazy load, formatos |
| `/seo-image-gen` | Cria plano de geração de imagens OG e sociais | Melhorar preview em redes sociais |
| `/seo-sitemap` | Valida e gera XML sitemaps | Indexação e crawl budget |
| `/seo-flow` | Aplica framework FLOW de otimização em etapas | Otimização estruturada por estágio |
| `/seo-drift` | Detecta regressões comparando com baseline capturado | Monitorar mudanças não intencionais |
| `/seo-maps` | Rastreamento de ranking em grade geo, GBP e reviews | SEO local avançado |

---

## Gstack (Navegador)

> Acesso headless ao Chrome para ler e pesquisar conteúdo na web.

| Comando | O que faz | Quando usar |
|---|---|---|
| `/browse` | Navega e lê páginas no Chrome headless | Ler artigos, URLs e páginas para ingerir no wiki |
| `/connect-chrome` | Conecta ao Chrome já aberto | Reutilizar sessão já autenticada |
| `/setup-browser-cookies` | Configura cookies de autenticação | Acessar conteúdo pago ou protegido |
| `/learn` | Pesquisa guiada sobre um tema | Explorar um tópico novo para alimentar o wiki |
| `/investigate` | Investiga um tópico em profundidade com evidências | Pesquisa mais extensa com múltiplas fontes |
| `/office-hours` | Sessão de mentoria em dúvidas complexas | Decisões difíceis, análise de situações |
| `/setup-gbrain` | Configura integração com gstack | Setup inicial — rodar uma vez |
| `/gstack-upgrade` | Atualiza gstack para última versão | Manter skills atualizadas |

---

## Gstack / Produto & Ship

| Comando | O que faz | Quando usar |
|---|---|---|
| `/ship` | Fluxo completo de ship: testa, revisa, mergea e deploia | Subir uma feature para produção |
| `/land-and-deploy` | Faz landing de um PR e deploy | Após aprovação de PR |
| `/canary` | Deploy gradual com monitoramento de métricas | Release com risco controlado |
| `/qa` | Executa QA completo do app com browser | Antes de qualquer release |
| `/qa-only` | QA isolado sem outras operações | Testar uma feature específica |
| `/setup-deploy` | Configura pipeline de deploy do projeto | Setup inicial de CI/CD |
| `/landing-report` | Gera relatório pós-landing com métricas e status | Acompanhar resultado de um deploy |

---

## Gstack / Planejamento

| Comando | O que faz | Quando usar |
|---|---|---|
| `/spec` | Cria spec técnica detalhada para uma feature ou sistema | Antes de planejar implementação |
| `/autoplan` | Gera plano de implementação automaticamente a partir do contexto | Acelerar planejamento de tarefas |
| `/plan-ceo-review` | Revisa plano do ponto de vista de CEO/negócios | Validar alinhamento estratégico |
| `/plan-eng-review` | Revisa plano do ponto de vista de engenharia | Validar viabilidade técnica |
| `/plan-design-review` | Revisa plano do ponto de vista de design e UX | Validar experiência do usuário |
| `/plan-devex-review` | Revisa plano do ponto de vista de DX e tooling | Validar ergonomia para o time |
| `/plan-tune` | Refina e otimiza um plano existente | Melhorar plano antes de executar |
| `/retro` | Conduz retrospectiva de sprint ou feature | Aprender com o que foi feito |

---

## Gstack / Dev & Colaboração

| Comando | O que faz | Quando usar |
|---|---|---|
| `/codex` | Interface com OpenAI Codex para geração de código | Tarefas específicas de geração de código |
| `/pair-agent` | Modo pair-programming com agente especializado | Colaborar em código complexo |
| `/benchmark` | Mede e compara performance de implementações | Otimização de performance |
| `/benchmark-models` | Compara modelos de IA em tarefas específicas | Escolher o melhor modelo para uma tarefa |
| `/cso` | Chief Security Officer — análise de segurança estratégica | Revisão de arquitetura de segurança |
| `/devex-review` | Revisa experiência do desenvolvedor no projeto | Melhorar tooling e DX |
| `/closer-pitch-review` | Revisa pitch de vendas com foco em fechamento | Antes de apresentar para prospects |
| `/deep-research` | Pesquisa aprofundada sobre um tema com múltiplas fontes | Investigação demorada e abrangente |
| `/scrape` | Faz scraping de páginas e extrai dados estruturados | Coletar dados de sites |

---

## Gstack / Contexto & Manutenção

| Comando | O que faz | Quando usar |
|---|---|---|
| `/context-save` | Salva contexto de trabalho atual para continuar depois | Ao pausar uma tarefa longa |
| `/context-restore` | Restaura contexto salvo de uma sessão anterior | Ao retomar uma tarefa pausada |
| `/sync-gbrain` | Sincroniza estado do gstack/gbrain | Manter integração atualizada |
| `/health` | Verifica saúde geral do projeto e ambiente | Diagnóstico rápido do estado |
| `/open-gstack-browser` | Abre o browser do gstack headless | Inspecionar estado do browser |

---

## Gstack / Skills & Controle

| Comando | O que faz | Quando usar |
|---|---|---|
| `/skillify` | Cria nova skill a partir de um padrão de uso recorrente | Automatizar comportamento que você repete |
| `/skill-creator` | Interface avançada para criar e editar skills | Criar skills complexas |
| `/freeze` | Congela mudanças — impede alterações no projeto | Período de estabilização antes de release |
| `/unfreeze` | Descongela o projeto após período de freeze | Retomar desenvolvimento |
| `/guard` | Ativa guarda ativa — monitora e rejeita mudanças perigosas | Proteger código crítico |
| `/careful` | Modo cauteloso — confirma antes de cada ação destrutiva | Operações de alto risco |

---

## Claude API

| Comando | O que faz | Quando usar |
|---|---|---|
| `/claude-api` | Referência completa da Claude API: modelos, preços, streaming, tool use, MCP, caching | Qualquer tarefa com Claude/Anthropic API |
