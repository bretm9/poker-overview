# Texas Hold'em — heads-up poker against five AI opponents

> A complete single-player Texas Hold'em game in the browser: shuffling, blinds, a rotating dealer button, all four betting rounds, best-5-of-7 hand evaluation, and a showdown — against five AI opponents who fold, call, and raise on hand strength. Mobile-first, with a felt table, dealing animations, chips that slide to the pot, and a raise slider with pot-fraction presets.

🔗 **Play it:** https://poker-ebon-two.vercel.app

This repo is an overview of a closed-source project (I built it because free, ad-less, no-login poker apps are surprisingly hard to find). The source is private — I'm happy to walk through it in an interview.

<p align="center">
  <img src="screenshots/table-desktop.png" width="900" alt="Poker table">
</p>

---

## Screenshots

<p>
  <img src="screenshots/mobile-preflop.png" width="230" alt="Pre-flop">
  <img src="screenshots/mobile-flop.png" width="230" alt="Flop">
  <img src="screenshots/mobile-showdown.png" width="230" alt="Showdown">
</p>

## Features

- **Full hand loop** — deck shuffle, small/big blinds, rotating dealer button, pre-flop / flop / turn / river betting rounds with correct action order, and a showdown with the winning hand named.
- **Hand evaluator** — best five of seven cards across all ranks (high card through straight flush) with kicker tie-breaks.
- **Five AI opponents** who decide fold / call / raise from hand strength and the current bet, with a little variance so they're not predictable.
- **Betting UI** — check/call/fold buttons, a raise slider with pot-fraction presets, and an action log ("Emma folds", "David checks").
- **Table presentation** — felt texture, card-dealing animations, animated chip-to-pot movement, avatar seats with stack sizes, and a layout that works portrait on a phone or wide on a desktop.

## Technologies

React · TypeScript · Vite · Tailwind CSS · Vercel

## Engineering notes

- The game state is a single reducer-style model (players, deck, community cards, phase, active player, bets) so every UI element derives from one source of truth and the AI turns can be scheduled deterministically.
- Betting-round completion is tracked explicitly (who has acted since the last raise) — the part of Hold'em most homemade implementations get subtly wrong.
- Animations are decoupled from game logic: bets animate to the pot after the state has already moved on, so the game never waits on a transition.

## Status

Built October 2025 (~950 lines). Live.

## Process

Built solo with Claude Code as a pair-programmer.

---

*Bret Merritt · [GitHub](https://github.com/bretm9) · [LinkedIn](https://www.linkedin.com/in/bret-merritt) · merrittbret9@gmail.com*
