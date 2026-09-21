# Agent instructions — Elemental Guardians

Applies repository-wide unless a closer `AGENTS.md` provides additional guidance. Official BMAD skills live under `.agents/skills/`; do not modify installer-managed files for project-specific process changes.

## Product and context
- Reviewed product requirements: `docs/game-design.md`; technical design: `docs/architecture.md` and `docs/data-contracts.md`. Read only relevant sections. These documents describe intended behavior and architectural decisions, **not whether a feature has been implemented**.
- Android landscape single-player, one actively fighting hero per run, 20 fixed waves, 10–15-minute target; Kael is free; Lyra/Varek can be earned with fragments or purchased individually and intentionally provide gameplay advantages. Four disciplines, 11 planned towers.
- Use original artwork, code, maps, names, UI and sounds. Never copy Warcraft III or Element TD assets, maps, source, branding or distinctive presentation.
- Combat runs locally. Backend authority for durable progression, fragments and purchase entitlements; validate purchases server-side and make rewards/unlocks idempotent. Client-reported combat results are not proof of legitimate play.

## One source of truth for the *current* state
- **Never infer implementation status from README files, design docs, roadmaps, BMAD planning artifacts or previous conversations.** They are plans, instructions or historical records, not a live progress dashboard.
- For the task at hand, inspect the latest target branch (`main`), relevant source/tests/configuration and the linked GitHub Issue/PR. Determine which files, components, checks and tooling actually exist **at the time of the task**. If access to GitHub or the checkout is unavailable, state the limitation instead of guessing.
- The current branch's code/configuration is the source for implemented behavior; the Issue and linked PR are the source for work status and approval; actual test/CI results are the source for verification. An open PR does **not** mean its changes are in `main`.
- Do not copy temporary states such as "not installed", "no stories approved", "next story" or "X implemented" into permanent docs. Do not maintain duplicate progress checklists or an independently updated sprint status in multiple Markdown files. If an official BMAD workflow requires a sprint tracking artifact, treat it as a derived view and reconcile it against GitHub before use; GitHub remains operational authority.

## BMAD planning → GitHub Issues → Codex → human merge
- Follow `docs/development/workflow.md` and `docs/development/definition-of-done.md` for the project process; use the **installed official BMAD workflows** for planning, without editing installer-managed skills.
- Reviewed design docs are inputs. BMAD PRD, architecture and epics/stories live at the installed/configured output location. A reviewed BMAD story is the implementation specification; its GitHub Issue is the operational ticket with consistent acceptance criteria and a reference to that story. Search existing Issues before creating new ones.
- Before coding: pick exactly one **owner-approved Ready** Issue (or approved isolated bug/technical task), inspect its dependencies and current `main`, and create `feature/<issue-number>-<slug>` (or `fix/<issue-number>-<slug>`) from latest `main`. Never implement gameplay directly on `main`.
- Implement criteria and focused tests; open PR against `main`, reference the Issue using `Closes #<number>` when complete, and include test evidence/limitations. **Never merge your own PR, bypass checks or call an Issue Done before owner approval and merge.** Do not create or merge implementation PRs in a story-generation-only task.
- Operational workflow states are defined in `docs/development/workflow.md`. Update GitHub; do not claim manual BMAD tracking is automatically synchronized.

## Token-efficient engineering
- One story per implementation session. Read this file, the Issue, its relevant BMAD story and the task-relevant code/docs. Do not reload the whole PRD or reconstruct progress from documentation.
- When a real Unity project is present, put gameplay code under `Assets/Game/`; backend code belongs under `backend/`. Separate simulation/rendering, run saves/account state and earned ownership/paid entitlements.
- Never fabricate a working Unity project, SDK, CI checks or passing tests. State what ran, on which revision/environment, and which validation could not run. Add focused tests for damage, wave state, saves, rewards, unlocks and billing as appropriate.
- Never commit secrets, service accounts, keystores, live receipts, personal data or generated `Library/`, `Temp/`, `Obj/`, `Build/` directories.
- Report concisely: changed files, tests/results, blockers and PR URL. Token savings must not remove necessary security or acceptance checks.

## Change control
- If an Issue conflicts with reviewed product or technical decisions, flag the conflict before changing scope. Approved decisions update affected design docs and, where significant, an ADR in `docs/decisions/`.
- Follow `docs/development/testing-strategy.md`; trust actual checks on the relevant commit rather than any written claims about CI availability.
