# Copilot instructions

## Project structure

This is a dependency-free, single-page space quiz. The complete app lives in `index.html`: its semantic markup defines the welcome, quiz, and results screens; inline CSS provides layout, animation, and themes; and inline JavaScript owns the question data and quiz state. Keep it directly runnable as a local file unless the project scope changes.

The quiz flow is a small state machine: `startQuiz` resets state, `renderQuestion` displays the current item from the `questions` array, `selectAnswer` records a choice, `checkAnswer` updates score and progress, and `showResults` displays the final reaction. Each question's `correct` value is a zero-based index into that question's `answers`.

## Build, test, and lint

There are no configured build, test, or lint commands. Open `index.html` directly in a browser; no server or dependencies are needed.

For a focused browser smoke check:

- Start the quiz and navigate with Tab and Enter.
- Check both a correct and incorrect answer; verify score, feedback color, and progress.
- Complete all ten questions and verify the final score and results reaction.
- Check both `prefers-color-scheme` themes and reduced-motion behavior after style changes.

## Implementation conventions

- Keep the question content in the `questions` array and preserve its answer-index mapping when editing choices.
- Keep styling in the existing inline `<style>` block and use the CSS custom properties for theme-dependent colors. The light palette is defined by `prefers-color-scheme: light`; retain the dark default.
- Keep the screens in the document and toggle them with the existing `.hidden` class. Quiz progress and answer feedback are exposed through ARIA attributes/live regions.
- Preserve keyboard focus handoff: focus the question heading when a quiz starts or advances, and focus the Play again button when results appear. Use native buttons for actions and keep decorative icons hidden from assistive technology.
- Respect the existing `prefers-reduced-motion` rule when introducing or changing animation.
