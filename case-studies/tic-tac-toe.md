# Tic-Tac-Toe · Neon Arena — clean state management with an unbeatable CPU

**Type:** Frontend intern assignment · **Solo**
**Live:** [tic-tac-toe-five-ebon-96.vercel.app](https://tic-tac-toe-five-ebon-96.vercel.app/) · **Code:** [github.com/Qhawekazii/tic-tac-toe](https://github.com/Qhawekazii/tic-tac-toe)
**Stack:** React 19 · `useReducer` · Vite · Vercel

---

## The problem

The brief was "build Tic-Tac-Toe" — a common exercise. The real problem underneath it is state: board, turn, winner, scores, mode, difficulty, player names and move history all change together, and spreading them across many `useState` calls quickly leads to bugs where the screen and the rules disagree.

## What I built

- **All game state in one reducer** with named actions (`PLAY`, `JUMP_TO`, `RESTART`, `SET_MODE` …), so every change goes through one place.
- **One function decides the result.** `getGameStatus()` is the only code that decides winner / draw, and both the reducer and the UI use it — they can't disagree.
- **Two players or vs CPU.** Easy mode picks a random square. Hard mode uses the **minimax** algorithm to play out every possible game, so it can't be beaten.
- **The CPU follows the same rules as you.** It doesn't change state directly; it picks a square and dispatches a normal `PLAY` action.
- **Time travel.** Click any move in the history to see the board at that point; playing from there drops the old future.
- **Player names, a scoreboard, and a neon theme** — with animations that switch off for anyone who has reduced motion turned on.

## Outcome

A small game with the same architecture you'd want in a larger app: one source of truth, presentational components that only render props, and rules that live in exactly one place.
