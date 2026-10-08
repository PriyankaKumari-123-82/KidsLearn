# KidsLearn

A playful, offline-first learning app for children ages 4–12, built with Expo and React Native.

## MVP features

- Five quiz subjects with shuffled answer choices, instant supportive feedback, rounds of up to 10 distinct questions, and adaptive difficulty. All subjects can generate offline variants from bounded math rules or reviewed word/fact templates.
- Rhyme Time with Pop the Rhyme, Rhyme Pairs, and Finish the Rhyme modes, read-aloud speech, a sound toggle, and stars shared with the other games.
- Age-band content selection for ages 4–5, 6–8, and 9–12.
- 4×4 and 6×6 Sudoku with row/column/box checks, hints, undo, and bundled puzzles verified to have one solution.
- Shared stars and streaks, plus a family progress screen with quiz, rhyme, and puzzle summaries.
- Progress, age-band, and rhyme sound preference saved locally using AsyncStorage; play does not require an account or network connection.

Questions are generated locally without a live AI call. Math and numeric patterns use computed rules in `src/engine/generators.ts`; English, Science, and General Knowledge create choice variants from bounded word and fact templates in `src/engine/subjectGenerators.ts`. These templates are a starter set and should receive educator review before release or curriculum claims. Question order and answer choices are shuffled. Previously seen IDs are saved and deprioritized until a pool is exhausted. This is not yet a complete or curriculum-reviewed content library. The 9×9 grid, notes mode, time limits, bedtime lock, data export/deletion controls, parent PIN, and backend sync are not implemented. Progress is device-local, so it is not backed up or shared between devices. Before publishing for children, complete a privacy/legal review and add the required parental controls and consent flow.

## Run the app

1. Install Node.js and npm.
2. Run `npm install` from this project directory.
3. Run `npm start` and open the project in Expo Go by scanning the terminal QR code, or use `npm run android` with an Android emulator/device configured.
4. Run `npx tsc --noEmit` to check TypeScript.

The iOS simulator build requires macOS. No backend, analytics, advertising, or account service is configured.

## Project layout

- `App.tsx`: Home, quiz, Sudoku, Rhyme Time, and family progress screens.
- `src/components/RhymeGame.tsx`: Playable rhyme modes and text-to-speech controls.
- `src/data/rhymes.ts`: Bundled original rhyming word pairs and short poems.
- `src/data/questions.ts`: bundled starter question bank.
- `src/engine/quiz.ts`: question selection, answer shuffling, and adaptive level logic.
- `src/engine/sudoku.ts`: puzzle setup, solver, uniqueness validation, and board rules.
- `src/engine/subjectGenerators.ts`: offline English, Science, and General Knowledge word/fact templates.
- `src/store/progress.ts`: local progress persistence.
