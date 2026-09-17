# Minesweeper

Classic Minesweeper built with React, TypeScript, and Vite. Purely client-side.

## Quick Start

```bash
npm install
npm run dev
```

## Scripts

| Command | Description |
|---------|------------|
| `npm run dev` | Start dev server |
| `npm run build` | Type-check and build for production |
| `npm run preview` | Preview production build locally |
| `npm test` | Run unit tests |
| `npm run test:watch` | Run tests in watch mode |

## Deploy (Vercel)

```bash
npm run build
vercel --prod
```

Or push to GitHub and import in the Vercel dashboard — Vite projects are auto-detected.

## Gameplay

- **Easy**: 9×9, 10 mines
- **Medium**: 16×16, 40 mines
- **Hard**: 25×25, 150 mines

Left-click to reveal, right-click to flag. On touch devices, toggle Flag Mode with the 🚩 button.

## Project Structure

```
src/
  game/           Pure game logic + types + constants
    tests/          Gameplay & UI tests
  hooks/          useGame (state reducer), useTimer
  components/     Board, Cell, StatusBar, DifficultySelector
  styles/         Single CSS stylesheet
  test-setup.ts   Vitest + Testing Library setup
```

## Testing

Tests use [Vitest](https://vitest.dev/) with [Testing Library](https://testing-library.com/) for component tests and `jsdom` for DOM simulation.

### Test files

| File | Type | Covers |
|------|------|--------|
| `src/game/logic.test.ts` | Unit | Core logic (createEmptyBoard, placeMines, revealCell, toggleFlag, checkWin, countFlags) |
| `src/game/tests/gameplay.test.ts` | Unit | Advanced logic (getNeighbors, flood-fill, edge cases, full game simulation) |
| `src/game/tests/Cell.test.tsx` | Component | Cell rendering (hidden, flagged, revealed, mine, numbered), interactions |
| `src/game/tests/Board.test.tsx` | Component | Board grid, index passing, grid styles, wrong flags, disabled states |
| `src/game/tests/StatusBar.test.tsx` | Component | Counters, status emoji, flag mode toggle, value padding/clamping |
| `src/game/tests/DifficultySelector.test.tsx` | Component | Button rendering, active highlight, onChange |
| `src/game/tests/App.test.tsx` | Integration | Full app rendering, difficulty switching, cell reveal/flag, board sizes |