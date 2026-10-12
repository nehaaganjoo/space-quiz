# Repository guidance

## Application shape

This is a single-page, dependency-free space quiz. The complete app lives in `index.html`: semantic HTML shell, inline CSS, and vanilla JavaScript. There is no package manifest, build pipeline, or multi-file application architecture.

The `questions` array is the quiz content source. `renderQuestion()` draws the current question, `selectAnswer()` handles scoring and feedback, and `renderResults()` displays the final score and rank. Quiz state is held in the `current`, `score`, and `answered` variables.

## Build and test

- There are no repository build, test, or lint commands.
- Open `index.html` directly in a browser; no server or dependency installation is needed.
- For behavior changes, smoke-test the quiz in the integrated browser: answer questions through the results screen and check feedback, score, progress, replay, and keyboard operation.

## Project-specific conventions

- Keep the app self-contained in `index.html`; use inline CSS and vanilla JavaScript rather than adding a framework or build tooling.
- Keep question text, answer choices, correct-answer indexes, and explanations together in the `questions` array. Correct-answer indexes are zero-based.
- Render question and result views from the existing functions, and bind handlers to the newly rendered controls there.
- Preserve the light/dark color-token pairs in `:root` and `@media (prefers-color-scheme: dark)`. Keep animation changes compatible with `@media (prefers-reduced-motion: reduce)`.
- Preserve native button controls, the quiz progress bar semantics, live feedback, and focus movement between answers, the next action, new questions, and results. Number keys 1–4 select answers and Enter continues after feedback.
