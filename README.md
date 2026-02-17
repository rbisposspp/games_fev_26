# games_fev_26

Portuguese + English README for the ESL web tools.

## Visão geral (PT)

- `game.html`: jogo de associação de verb phrases com timer, dicas e progresso.
- `stations.html`: rotação de 4 estações (Listen, Guess, Visual, CCQ) com TTS, timer, notas e import/export.

## Overview (EN)

- `game.html`: verb phrase matching game with timer, hints, and progress.
- `stations.html`: 4-station rotation (Listen, Guess, Visual, CCQ) with TTS, per-station timer, notes, and JSON import/export.

## Demo local / Local demo

Sem build pipeline / No build step needed:

```bash
python -m http.server 8000
```

Acesse / Open:

- `http://localhost:8000/game.html`
- `http://localhost:8000/stations.html`

Windows (abrir direto) / Windows (quick open):

```bash
start game.html
start stations.html
```

## Estrutura / Structure

```text
.
├── AGENTS.md
├── game.html
└── stations.html
```

## Funcionalidades / Features

### game.html

- PT: Matching com feedback, atalhos (`R`, `S`, `H`), timer com melhor tempo em `localStorage`.
- EN: Matching with feedback, shortcuts (`R`, `S`, `H`), session timer with best time in `localStorage`.

### stations.html

- PT: 4 estações, timer por estação com avanço automático, TTS (Web Speech API), notas e KPIs, import/export JSON validado.
- EN: 4 stations, per-station timer with auto-advance, TTS (Web Speech API), notes and KPIs, validated JSON import/export.

## Persistência local / Local reset

Console do navegador / Browser console:

```js
// game.html
localStorage.removeItem("verb_phrase_match_best_time_sec");

// stations.html
localStorage.removeItem("eslStations_v1");
localStorage.removeItem("eslStations_items_v1");
```

## Tecnologias / Stack

- HTML5
- CSS3
- JavaScript (vanilla)
- Web Speech API (quando suportado / when supported)

## Contribuição / Contributing

1. Fork.
2. Branch de feature / feature branch.
3. Commit.
4. Pull Request com / with:
   - resumo / summary
   - impacto para usuário / user impact
   - passos de teste manual / manual test steps
   - screenshots/GIFs para UI

## Status

PT: Funcional offline/local, sem dependências externas obrigatórias.  
EN: Works offline/local; no external dependencies required.
