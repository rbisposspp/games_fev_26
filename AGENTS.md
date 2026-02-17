# Repository Guidelines

## Project Structure & Module Organization
This repository is a lightweight static web project.
- `game.html`: verb phrase matching game UI and logic (stats, hints, shortcuts, progress, best-time persistence).
- `stations.html`: ESL stations planner UI and logic (station timer, TTS, import/export, local progress state).

Files currently live at the repository root. If shared assets are added, place them in `assets/` (for images/fonts) and keep page-specific scripts/styles close to their page unless reuse is clear.

## Build, Test, and Development Commands
No build pipeline is required.
- `python -m http.server 8000` - serve files locally.
- Open `http://localhost:8000/game.html` or `http://localhost:8000/stations.html` in a browser.
- `start game.html` (Windows) - quick local open without a server for simple checks.
- Browser console reset (game best time): `localStorage.removeItem("verb_phrase_match_best_time_sec")`.
- Browser console reset (`stations.html`): `localStorage.removeItem("eslStations_v1"); localStorage.removeItem("eslStations_items_v1")`.

## Coding Style & Naming Conventions
- Use semantic HTML and keep CSS/JS readable within each page.
- Match existing formatting: 2-space indentation in HTML/CSS/JS blocks.
- Prefer clear, descriptive IDs/classes (e.g., `station-list`, `score-pill`).
- Keep file names lowercase and descriptive (e.g., `lesson_planner.html`).
- For `game.html`, keep logic split into focused functions (rendering, state updates, timing, feedback) and avoid hidden side effects.
- For `stations.html`, keep imported/user-provided text rendered with `textContent` (avoid injecting strings into `innerHTML`).
- Preserve accessibility patterns already in use (`aria-live`, `aria-pressed`, `aria-disabled`) and reduced-motion support.

## Testing Guidelines
Automated tests are not configured yet; use manual smoke testing for every change:
- Verify both pages load without console errors.
- Check responsive behavior on desktop and mobile widths.
- Validate game flows: correct/incorrect matching feedback, selection clear behavior, progress updates, reset/shuffle, and hint highlighting.
- Validate keyboard shortcuts in `game.html`: `R` (reset), `S` (shuffle), `H` (hint).
- Confirm timer behavior: starts on reset, stops on win, and best time persists across refresh via localStorage.
- Validate `stations.html` primary flows: timer start/pause/auto-rotate, station navigation, notes save, import/export, and reset behavior.
- Confirm `stations.html` import constraints: JSON array with required fields and at least 3 items.
- Verify `stations.html` score stays consistent after answer retries.
- Verify `stations.html` TTS fallback in unsupported browsers and timer persistence after refresh.

When fixing bugs, include reproducible steps and expected result in your PR notes.

## Commit & Pull Request Guidelines
Git history is not available in this directory, so follow a consistent convention:
- Commit subject: imperative and concise, preferably Conventional Commits (`feat:`, `fix:`, `chore:`).
- Keep related changes grouped in one commit.
- PRs should include: summary, user-facing impact, manual test steps, and screenshots/GIFs for UI updates.

## Security & Configuration Tips
- Do not hardcode secrets, tokens, or private URLs in HTML/JS.
- Sanitize and validate user-provided text before rendering.
- Keep localStorage usage non-sensitive (game stats only; no personal or secret data).
- For imported JSON in `stations.html`, validate structure before saving and treat all text as untrusted input.
- Keep third-party dependencies minimal; document any added external scripts.
