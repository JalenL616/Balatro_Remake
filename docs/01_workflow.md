# Working Method

Status: Draft v0, written 2026-11-09. Revisit at the week-1 checkpoint. Goals and terms are defined in `00_charter.md`; the evidence behind several choices is in `03_research_notes.md`.

## Roles
- **Owner:** decides game mechanics and writes or reviews specs. Writes or reviews every expected value in tests. Reads the code and asks questions about it.
- **AI assistant:** implements, pushes back on specs, and reconsiders its implementation when the owner's questions expose a problem.
- **Where the owner writes code:** decided piece by piece. The default is that the owner writes first attempts of small pieces, especially anything involving debugging, and the assistant writes larger or repetitive pieces. The owner can ask to switch either way at any time.

## Two kinds of work
1. **Main branch (pair programming from a spec).** Spec first, then the assistant and owner build together, with the code read and questioned as it goes.
2. **Vibe branch (throwaway experiment).** The owner writes a spec; the assistant implements that same spec with little back-and-forth on a separate git branch named `vibe/<item>`. The owner then reviews it with intern-level rigour and compares with the main-branch version. Lessons feed the main build. The branch is deleted afterwards. Reviews are mandatory and time-boxed (default 30 to 45 minutes; adjust after the first one).
   - Why: seeing a full AI solution before designing anchors the owner's own design. Writing the spec first and comparing afterwards avoids that.

## Spec format (specs and tests are one document)
Each requirement is one entry that maps to test cases, so there is no second list to keep in sync:

```
### REQ-<n>: <one line>
Source: <URL or wiki page; write "owner memory" if none>
Rule: <plain statement of the behaviour>
Tests:
- T<n>.1: given <input>, expect <value>   (expected value set or reviewed by the owner)
Status: draft | approved | implemented | explained
```

Sources can disagree on details (for example when vouchers take effect). When they do, the owner picks one, and the test records which source it follows.

## Question protocol
After the assistant produces code, the owner asks specific follow-up questions about it (why this structure, what breaks if it changes, where would a bug in X show up) before moving on. The assistant answers, and reconsiders the code if a question reveals a flaw. Research supports this pattern: in a randomized study, people who generated code with AI and then asked follow-up questions kept far more understanding than people who delegated fully (see `03_research_notes.md`). Treat that as supporting evidence to test on this project, not as proof.

## Explain-back rubric v0
Run after an item's tests pass. The code stays closed.
1. Explain in your own words what the item does and why it is structured that way (about 2 minutes).
2. Answer two debugging-style questions from the assistant, for example "this output is wrong; where do you look first?" or "what breaks if this rule changes?".
3. Predict the effect of one small proposed change before running it.

Scoring: **pass** if all three are done without opening the code. **Partial** if one fails; note the gap, and it becomes a review item next sprint. **Fail** if two or more fail; re-read the code and repeat the check later.

Limits to keep in mind: the assistant both wrote the code and asks the questions, so the check is not independent. The owner's honest self-score is the record. The rubric must be fixed before a sprint starts, not adjusted mid-sprint to make an item pass. This rubric is untested; revise it after sprint 1.

## Vibe-branch review checklist v0
- Does every requirement in the spec have a test? Do the tests assert the owner's expected values?
- Can you say in one sentence what each file or function is for?
- Does the engine code avoid importing UI code?
- Does any randomness bypass the seeded streams?
- Is any logic duplicated, or any magic number unexplained?
- Which edge cases are untested?

Output: a three-line note of defects found, time spent, and what to take into the main branch.

## Sprint cadence
- **Start:** choose items sized to the 1 hour a day floor (about 7 hours a week). Fix the explain-back rubric.
- **During:** work item by item; run explain-back as each item finishes.
- **End (5-minute retro):** record planned vs. done items; explain-back passes out of attempts; vibe-branch findings if any. Set next week's hours. Update this document if the method needs changing.
- Commit to the floor, never the stretch. A missed commitment is data, not failure.
