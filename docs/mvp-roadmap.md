# MVP roadmap and story-seeding checklist

## M0 — Official toolchain/bootstrap
- Install supported Unity LTS via Unity Hub and **create an actual Unity project in this repository**, retaining engine-created `Assets/`, `Packages/`, `ProjectSettings/` and `.meta` files. Commit editor/package version after validating them. Do not fabricate Unity metadata or manifests.
- Install official BMAD as documented in `docs/development/bmad-codex.md`, invoke `bmad-help`, produce/review BMAD PRD, architecture, epics and stories according to installed workflows. Align them with `docs/game-design.md`.
- Select backend language/runtime, test runner, project package names, Android device matrix and real commands in an ADR; do not assume they already exist.

## M1 — Vertical slice (first implementation target)
One original map and path, basic tower build/upgrade, one enemy + fixed 5-wave sequence, base HP, gold economy, Kael movement/autoattack/one active ability, pause/restart, Android touch UI. **Acceptance:** compile and play on real Android device; defeat/victory flow; no unhandled errors in baseline run. No commerce or cloud required for M1.

## M2 — Full combat design
20 fixed waves, 8 opponent archetypes and boss, 4 elements and all 11 towers, 4 bounded resonance interactions, three difficulty tiers (tune normal first), Lyra and Varek and ability tests. **Acceptance:** Kael can complete normal with skilled play; fixed wave content repeats across runs; 10–15 minute target tested.

## M3 — Progression + persistence
Local atomic resumable run snapshots; authenticated player profile, earned fragments, mastery, backend transactional unlock. **Acceptance:** app restart resumes a run; repeated run-claim/unlock requests do not double-grant or double-spend; recovered account retains heroes.

## M4 — Commerce
Google Play one-time hero product integration; server verification, pending state, acknowledgement, restore, refund/revocation and independent earned ownership. **Acceptance:** sandbox end-to-end lifecycle and duplicate/retry tests succeed; do not launch without them.

## M5 — Production readiness
Original art/audio/UI and onboarding; instrument optional privacy-conscious gameplay metrics; device profiling, accessibility/localization decisions, privacy/legal/IP review and Play policy review. **Acceptance:** documented device/build test evidence and release checklist signed off.

## Story template / definition of ready
Each generated BMAD story must include: user goal and rationale; references to relevant source-of-truth sections; precise scope and exclusions; examples and boundary cases; testable acceptance criteria; dependencies and data/schema migrations; verification command/device; security and purchase implications. A story is done only after actual verification and documentation of untested limitations.
