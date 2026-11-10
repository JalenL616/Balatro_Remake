# Project Charter: Balatro Remake

Status: Draft v0, written 2026-11-09. Revisit at the week-1 checkpoint. Anything here can change when the owner says so; until then it counts as settled.

## What this is
A remake of Balatro in the browser using React. Balatro is a poker-based roguelike deckbuilder: the player plays poker hands to beat a score target each round, earns money, and buys jokers (cards that modify scoring), consumables and upgrades between rounds. The project is solo and private.

## Intent
A learning vehicle and a game the owner enjoys, built for as long as motivation lasts. The owner knows Balatro's rules well and owns the game mechanics and specs. The AI assistant does most of the implementing and pushes back on specs. Login and player-versus-player play may be added much later purely as learning exercises, with no real users.

## Goals (ranked, with one measure each)
If goals collide, the higher one wins.

1. **Momentum**: keep building steadily and keep commitments. Measure: planned vs. done items per sprint. Aim for about 80%; always hitting 100% means the commitments are too small.
2. **Engineering instincts**: improve design judgment through doing, expert takes and feedback. Measure: explain-back pass rate (defined in `01_workflow.md`).
3. **AI-assisted coding workflow**: learn which ways of working with the assistant keep understanding intact. Measure: on branch experiments (see `01_workflow.md`), defects found in review and the share of spec requirements that have a test.

## Scope
- **In:** the whole game's rules (jokers, decks, stakes, vouchers, consumables, booster packs, blinds, tags), built in chunks. UI shortcuts are fine, since the UI is not the focus.
- **Platform:** desktop browser first. Mobile later, as a separate exercise.
- **Randomness:** the project's own deterministic seed. The same seed must always give the same game. Separate purposes get separate random streams, so for example the order of jokers offered in the shop is independent of the order of cards drawn from a tarot pack. Exact match with the real game's seeds is not required (it is parked, see `02_roadmap.md`).
- **Out for now (parked):** the ML bot, login/PvP/backend, mobile, exact seed parity. See `02_roadmap.md` for each one's problem statement.

## Constraints
- **Time:** 1 hour a day is the commitment floor; about 2 hours a day this week as a stretch. Adjusted weekly. Plans are sized to the floor, never the stretch.
- **Skills:** the owner has built one vibe-coded React and TypeScript project, so knows the rough structure but wants the core concepts and design practice, learned while building specs.
- **People:** solo.
- **Sources:** official wikis and documentation, plus the owner's knowledge of the game, until they prove insufficient. Where sources disagree, the owner decides and the choice is cited next to the test (see `01_workflow.md`).

## Success criteria
- **Item done:** its tests pass and the owner can explain it with the code closed (rubric in `01_workflow.md`).
- **Sprint done:** a sprint is about one week. It is done when its committed items are done. Missed items roll over; the miss is recorded in the retro, not hidden.
- **Original first target** (Ante 1 Small Blind of the default Red Deck, White Stake setup playable by Friday 2026-11-13) is retired as a hard date. Progress matters more than the date. The target remains the first milestone; see `02_roadmap.md`.

## Decisions so far
- Engine code does not import React. The reason is testability: rules tests run without a browser. (A future bot would benefit too, but that is not the reason.)
- Tests for rules, standard deck behaviour and seeded randomness are sourced from wikis and each cites its source. The owner writes or reviews every expected value, so tests are independent of the code the assistant writes.
- The ML bot (a program that plays full runs) is a parked idea, to be revisited when it will not compete for attention.
- Stack (TypeScript yes or no, test runner) is not chosen yet. It is a joint decision with the assistant; Vitest and TypeScript are only suggestions.

## Terms used in these docs
- **Item:** one unit of work with a written spec and tests.
- **Sprint:** about one week of items.
- **Chunk:** a feature-sized group of items, such as "deck and shuffle".
- **Explain-back:** the check that the owner understands an item (defined in `01_workflow.md`).
- **Vibe branch:** a throwaway git branch where the AI builds from a spec with little pairing (defined in `01_workflow.md`).
