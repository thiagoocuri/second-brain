---
title: "Vlog Dual-Layer — Sistema de Registro da Jornada"
type: spec
created: 2026-06-15
updated: 2026-06-15
status: approved
---

## Contexto

Thiago Ccuri (17 anos, fundador solo da Avalyse, estudante 3º EM em SP) quer documentar sua jornada como empreendedor em formato vlog. Objetivos: desenvolver fluência verbal, criar arquivo pessoal para revisão futura, construir material autêntico para marca pessoal a longo prazo.

Restrições: janela de trabalho limitada (escola seg–sex 7:25–16:00), tendência ao perfeccionismo, sem equipamento adicional além do celular.

---

## Design

### Layer 1 — Captura Passiva

**O que é:** gravação casual ao longo do dia, sem compromisso de montar nada.

**Critério de captura:** "isso vai ser interessante ver daqui 2 anos?" Se sim, grava. Sem pensar em enquadramento ou qualidade.

**O que gravar:**
- B-roll do dia (escola, trabalho, deslocamento, ambiente)
- Momentos de cold call, demo, decisão relevante
- Pensamentos em voz alta enquanto faz alguma coisa
- Resultados — bons e ruins

**Regra de seleção:** ainda no celular, depois de gravar, escolhe os clipes que valem e descarta o resto. Não é necessário guardar tudo — só o que teria valor de arquivo.

**Armazenamento:** Drive em `Vlog/Raw/YYYY-MM/`. Upload direto do celular, sem passar pelo PC.

---

### Layer 2 — Episódio Intencional

**O que é:** vídeo montado quando acontece algo que vale registrar.

**Gatilhos (exemplos):**
- Primeira demo com prospect real
- Primeiro cliente pagante
- Decisão difícil tomada
- Semana que ensinou algo concreto
- Resultado — positivo ou negativo com lição clara

**Formato fixo:**
1. Abertura to-camera — 30 a 60s explicando o que rolou e por que importa
2. B-roll do evento — clipes capturados no Layer 1 daquele período
3. Fechamento reflexivo — 30s de lição ou próximo passo

**Duração alvo:** 2 a 4 minutos.

**Edição:** CapCut no celular. Teto rígido de 30 minutos de edição — se passou disso, corta mais, não refina mais. Isso é o antídoto ao perfeccionismo.

**Nomenclatura:** `YYYY-MM-DD-[tema].mp4` (ex: `2026-06-20-primeira-demo.mp4`)

**Armazenamento:** Drive em `Vlog/Episódios/`.

---

### Estrutura no Drive

```
Vlog/
├── Raw/
│   ├── 2026-06/
│   ├── 2026-07/
│   └── ...
└── Episódios/
    ├── 2026-06-XX-[tema].mp4
    └── ...
```

---

### Decisão de Publicar

Não definir plataforma agora. Após **10 episódios completos**, revisar o arquivo e decidir:
- Vale publicar?
- Em qual plataforma faz sentido naquele momento?
- Com qual identidade/ângulo?

Isso evita o padrão de criar canal → postar 2 vídeos → sumir. A decisão de publicar é separada da decisão de gravar.

---

## Princípios

- **Zero fricção na captura** — Layer 1 não tem regras, só o celular
- **Teto de edição** — 30 min máximo, corta mais se precisar de mais
- **Arquivo primeiro, audiência depois** — os 10 episódios existem para você, não para ninguém
- **Episódio = evento, não calendário** — frequência é emergente, não planejada
