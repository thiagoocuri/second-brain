# Vlog Dual-Layer — Implementation Plan

> **Para execução:** siga as tarefas em ordem. Cada passo leva 2–5 minutos. Marque cada checkbox ao concluir.

**Goal:** Ativar o sistema de registro dual-layer (captura passiva + episódio intencional) com estrutura no Drive e primeiro clipe gravado no dia de hoje.

**Architecture:** Layer 1 é um hábito de captura sem fricção (celular → Drive). Layer 2 é um evento de produção disparado por gatilho, não por calendário. Os dois layers são independentes — Layer 1 existe mesmo sem nenhum episódio produzido.

**Tech Stack:** Google Drive (armazenamento), CapCut (edição no celular), câmera nativa do celular (captura).

---

### Task 1: Criar estrutura no Drive

**Arquivos/pastas:**
- Criar: `Vlog/Raw/2026-06/`
- Criar: `Vlog/Episódios/`

- [ ] **Passo 1: Abrir o Google Drive no celular**

- [ ] **Passo 2: Criar pasta `Vlog` na raiz do Drive**

- [ ] **Passo 3: Dentro de `Vlog`, criar pasta `Raw`**

- [ ] **Passo 4: Dentro de `Raw`, criar pasta `2026-06`**

- [ ] **Passo 5: Dentro de `Vlog`, criar pasta `Episódios`**

- [ ] **Passo 6: Verificar estrutura**

Resultado esperado:
```
Vlog/
├── Raw/
│   └── 2026-06/     ← pasta vazia, pronta para receber clipes
└── Episódios/        ← pasta vazia, pronta para receber episódios
```

---

### Task 2: Configurar celular para captura rápida

**Objetivo:** reduzir o atrito entre "quero gravar" e "estou gravando" para menos de 5 segundos.

- [ ] **Passo 1: Confirmar que o app Google Drive está instalado e logado**

- [ ] **Passo 2: Confirmar que o CapCut está instalado**

Se não tiver: instalar da App Store / Google Play.

- [ ] **Passo 3: Deixar a câmera nativa na tela inicial ou na barra de atalhos**

Câmera deve ser acessível sem desbloquear o celular (swipe da tela de bloqueio).

- [ ] **Passo 4: Criar atalho/marcador para a pasta `Vlog/Raw/2026-06/` no Drive**

No Drive mobile: abrir a pasta → três pontos → "Adicionar ao atalhos" ou "Fixar".

---

### Task 3: Gravar o primeiro clipe (hoje)

**Objetivo:** quebrar a inércia com o menor clipe possível — perfeição zero.

- [ ] **Passo 1: Pegar o celular agora**

- [ ] **Passo 2: Abrir a câmera e gravar 15–30 segundos de qualquer coisa**

Sugestões: o ambiente onde você está, o que está fazendo, um pensamento em voz alta sobre o projeto. Não precisa ser bom. O critério é: "seria interessante ver daqui 2 anos?" — se sim, grava.

- [ ] **Passo 3: Assistir ao clipe rapidamente e decidir se vale guardar**

Se não valeu: deleta e grava outro. Se valeu: próximo passo.

- [ ] **Passo 4: Fazer upload para `Vlog/Raw/2026-06/` no Drive**

No Drive: `+` → "Fazer upload" → selecionar o clipe.

- [ ] **Passo 5: Confirmar que o arquivo aparece na pasta**

Sistema está operacional.

---

### Task 4: Definir os próximos gatilhos de episódio

**Objetivo:** ter clareza sobre o que dispararia o primeiro Layer 2, sem compromisso fixo.

- [ ] **Passo 1: Pensar nos próximos 2–3 eventos que poderiam virar episódio**

Exemplos baseados no contexto atual da Avalyse:
- Primeira cold call V3 feita de verdade
- Primeira resposta positiva de prospect
- Primeira demo agendada
- Primeiro cliente pagante

- [ ] **Passo 2: Anotar esses gatilhos em algum lugar acessível**

Pode ser uma nota no celular, no Notion, ou num papel. O objetivo é que quando o evento acontecer, você lembre que é hora de montar um episódio.

- [ ] **Passo 3: Reler o teto de edição**

Regra inquebrável do Layer 2: **30 minutos máximo de edição**. Se passou, corta mais clipes — não refina mais. Isso protege contra perfeccionismo.

- [ ] **Passo 4: Memorizar a nomenclatura dos episódios**

Formato: `YYYY-MM-DD-[tema].mp4`
Exemplos: `2026-06-20-primeira-cold-call.mp4`, `2026-07-03-primeira-demo.mp4`

Salvar com esse nome direto no CapCut antes de exportar.

---

### Task 5: Criar rotina de upload semanal (opcional, mas recomendado)

**Objetivo:** garantir que clipes do celular não se percam antes do upload.

- [ ] **Passo 1: Escolher um dia e horário fixo para dump semanal**

Sugestão: domingo à noite, 5 minutos. Só mover clipes do rolo da câmera para `Vlog/Raw/YYYY-MM/` no Drive.

- [ ] **Passo 2: Criar lembrete recorrente no celular para esse horário**

Título: "Dump vlog — 5 min".

- [ ] **Passo 3: No primeiro dump, criar a pasta do mês seguinte antecipadamente**

Ex: na virada de junho para julho, criar `Vlog/Raw/2026-07/`.

---

## Critério de sucesso

O sistema está funcionando quando:
- [ ] Estrutura de pastas existe no Drive
- [ ] Pelo menos 1 clipe foi gravado e salvo em `Raw/2026-06/`
- [ ] Você sabe quais eventos disparariam o próximo episódio
- [ ] Depois de **10 episódios completos** em `Episódios/`, revisar se vai publicar e em qual plataforma
