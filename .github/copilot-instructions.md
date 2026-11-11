# Copilot instructions

## Project shape

- `index.html` is the complete app: semantic page markup, inline CSS, the question bank, and plain JavaScript. There is no separate application or build layer.
- The quiz replaces the contents of `#app` in `renderQuestion()` and `renderResults()`. Keep the theme control outside `#app`; question and result controls are created during rendering and have their event listeners attached there.
- Theme colors are CSS custom properties in `:root` and `:root[data-theme="dark"]`. `setTheme()` updates the root attribute and persists the selection in local storage, falling back to the system preference when there is no saved choice.

## Run and verify

- Open `index.html` directly in a browser. No server, dependency installation, build, lint, or automated test commands are defined.
- For a manual smoke check, start a mission, try correct and incorrect answers, confirm the score and progress update, finish all 10 questions, and use **Fly again**. Also check the theme toggle.

## Code conventions

- Keep quiz content in the `questions` array. Each entry has an `icon`, `question`, four `answers`, a zero-based `correct` answer index, and a `fact` used in feedback.
- Keep the question count and result thresholds derived from `questions.length`; answer indices must continue to match their displayed choices.
- Reuse the theme variables for new colors so additions work in both themes. The page uses a narrow, responsive layout and includes reduced-motion handling.
- Preserve native button controls and the existing accessibility pattern: hide decorative imagery from assistive technology, announce feedback with a live region, and keep the progress bar's ARIA value in sync with quiz progress.
- Keep the app self-contained in `index.html`; its Google Fonts import has system-font fallbacks and should not be required for the quiz to work.
