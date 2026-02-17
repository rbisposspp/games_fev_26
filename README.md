# games_fev_26

Projeto web estático com dois recursos para aulas de ESL:

- `game.html`: jogo de associação de verb phrases com timer, dicas e progresso.
- `stations.html`: rotação de 4 estações com TTS, timer, notas e import/export de conteúdo.

## Demo local

Como não há build pipeline, basta servir os arquivos estáticos:

```bash
python -m http.server 8000
```

Abra no navegador:

- `http://localhost:8000/game.html`
- `http://localhost:8000/stations.html`

No Windows, para abrir rápido sem servidor:

```bash
start game.html
start stations.html
```

## Estrutura do projeto

```text
.
├── AGENTS.md
├── game.html
└── stations.html
```

## Funcionalidades

### game.html

- Jogo de matching com feedback de acerto/erro.
- Atalhos de teclado (`R`, `S`, `H`).
- Timer de sessão com melhor tempo persistido em `localStorage`.
- Embaralhar/reiniciar sem build externo.

### stations.html

- 4 estações: Listen, Guess, Visual, CCQ.
- Timer por estação com avanço automático.
- TTS via Web Speech API (com fallback quando indisponível).
- Notas por item, persistência de progresso e KPIs.
- Importação/exportação JSON com validação básica.

## Persistência local (reset)

No console do navegador:

```js
// game.html
localStorage.removeItem("verb_phrase_match_best_time_sec");

// stations.html
localStorage.removeItem("eslStations_v1");
localStorage.removeItem("eslStations_items_v1");
```

## Tecnologias

- HTML5
- CSS3
- JavaScript (vanilla)
- Web Speech API (TTS, quando suportado pelo navegador)

## Contribuição

1. Faça um fork.
2. Crie uma branch de feature.
3. Commit suas mudanças.
4. Abra um Pull Request com:
   - resumo da mudança
   - impacto para usuário
   - passos de teste manual
   - screenshots/GIFs para alterações visuais

## Status

Projeto funcional para uso local/offline em sala de aula, sem dependências externas obrigatórias.
