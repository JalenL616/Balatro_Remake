# Roadmap and Parked List

Status: Draft v0, written 2026-11-09. Revisit at the week-1 checkpoint. Terms (item, sprint, chunk) are defined in `00_charter.md`; how items are specified and checked is in `01_workflow.md`.

## First milestone
"Ante 1 Small Blind playable": the default starting setup (Red Deck, White Stake, the base difficulty) lets a player play or discard from an 8-card hand against the first blind's score target and win or lose. This milestone is not tied to a date.

## Chunk order (from the owner's original plan)
Each chunk will be split into items, each with a spec and tests.
1. **Deck:** a 52-card deck where each card is an object with a suit and rank, easy to sort by either, and shuffleable with the seeded random generator.
2. **Hand:** dealing a hand (about 8 cards) from the deck.
3. **Selecting cards:** the UI to show the hand, click a card to preview it, and select cards, with the on-screen state matching the code.
4. **Poker hand values:** recognising poker hands and holding each hand type's base chips and multiplier, with levels that can increase.
5. **Scoring:** playing selected cards adds card values to the hand type's chips, then applies multipliers.
6. **Draw and discard:** the limited plays and discards per round, redrawing from the deck.
7. **Ante 1 Small Blind:** tie the above into one playable round.

Later chunks (not planned in detail): shop, jokers, booster packs, consumables, vouchers, boss blinds, tags, remaining decks and stakes.

## Candidate sprint 1 (to be confirmed before the sprint starts)
Chunk 1 (Deck) only: card and deck model, sorting, a seeded shuffle with the random generator kept behind one small interface so it can change later, and tests that cite their sources. Whether any UI is included is undecided.

## To settle before sprint 1 starts
- Stack: TypeScript or not, and the test runner. Suggestions only: TypeScript and Vitest.
- Sprint 1's exact item list, each with a spec and tests.
- The first commitment number (items for the week).
- Whether sprint 1 includes UI.
- Confirm the explain-back rubric in `01_workflow.md`, which is untested.

## Parked list (deliberately not decided now)
Each entry has a problem statement so it can be picked up cold.

| Parked item | Problem to solve when revisited |
|---|---|
| ML bot | A program that plays full runs. Needs a deterministic engine and a way to list legal actions. Unknown: algorithm, language (Python is usual for ML), and how it connects to the TypeScript engine. Revisit when the engine core works. |
| Login, PvP, backend | Accounts and player-versus-player play, as learning exercises with no real users. A different skill area (servers, data storage). |
| Mobile | A second platform as a separate exercise after the browser version works. |
| Exact seed parity | Making a seed reproduce the real game's runs. Much harder and needs reference material beyond the wikis. Not required. |
| Explain-back format | Possibly a mock interview or a short written report to make "can explain it" more formal and measurable. |
| More exemplar research | No source found on how many sprints similar clones took, or how they structure joker effects in code. Both would sharpen estimates. |
| Learning-science research | Not yet searched: retrieval practice, self-explanation, evidence on sprint velocity and commitment. |
| UI polish | Animations, sound and visual fidelity are intentionally low priority. |
