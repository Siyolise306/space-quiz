# Copilot instructions

## Project workflow

- The application is a standalone `index.html` with its markup, CSS, quiz data, and vanilla JavaScript in the same file. Open it directly in a browser; there is no build or server step.
- There is no package manifest or configured build, test, or lint command. To smoke-test a change, open `index.html`, start a quiz, try both a correct and an incorrect answer, advance through all 10 questions, and verify the score and results screen.
- Keep the app dependency-free and self-contained unless the project scope explicitly changes.

## Architecture and conventions

- The `questions` array is the source of truth for quiz content. Each question's `correct` value is a zero-based index into its `answers` array; keep the answer order and index in sync.
- The quiz flow is managed by `showWelcome`, `startQuiz`, `renderQuestion`, `chooseAnswer`, and `showResults`. Rendering replaces the contents of `#app`; `current`, `score`, and `answered` track quiz state.
- Styles are organized in the inline stylesheet and use CSS custom properties for shared colors. Keep light-mode tokens in `:root` and their dark-mode overrides in `@media (prefers-color-scheme: dark)`.
- Preserve the existing accessible interaction patterns: use native buttons for actions and answers, keep visible keyboard focus, update the progress bar's ARIA value, announce answer feedback through its status region, and honor `prefers-reduced-motion`.
- Keep feedback states distinct from theme accents: correct and incorrect answers use the dedicated green and red theme tokens, respectively.
