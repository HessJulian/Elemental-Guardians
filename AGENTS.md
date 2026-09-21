# Agent instructions — Elemental Guardians

Applies repository-wide unless a closer `AGENTS.md` provides additional guidance. Official BMAD skills live under `.agents/skills/`; do not modify installer-managed files to customize this project's process.

## Product and context
- Reviewed product baseline: `docs/game-design.md`; technical baseline: `docs/architecture.md` and `docs/data-contracts.md`. Read the relevant sections only. `docs/README.md` is the documentation index.
- Android landscape single-player, one actively fighting hero per run, 20 fixed waves, 10–15-minute target; Kael is free; Lyra/Varek can be earned with fragments or purchased individually and intentionally provide gameplay advantages. Four disciplines, 11 planned towers.
- Use original artwork, code, maps, names, UI and sounds. Never copy Warcraft III or Element TD assets, maps, source, branding or distinctive presentation.
- Combat runs locally. The backend is authoritative for durable progression, fragments and purchase entitlements; validate purchases server-side and make rewards/unlocks idempotent. Client-reported combat results are not proof of legitimate play.

## BMAD planning → GitHub Issues → Codex → human merge
- Read `docs/development/workflow.md` and `docs/development/definition-of-done.md` for the project-specific process. Follow the **installed official BMAD workflow** for planning; do not replace it with hand-written pseudo-BMAD commands or edit installer-managed skills.
- Existing reviewed docs are inputs. PRD, architecture and epics/stories produced by BMAD remain in the configured BMAD output location. A **reviewed BMAD story is the implementation specification**; its GitHub Issue is the operational ticket with matching acceptance criteria and a link to the versioned story file. Do not create duplicate Issues on reruns.
- Before coding: choose exactly one **owner-approved Ready** Issue with a linked BMAD story (or an approved isolated bug/technical task). Verify prerequisites and scope. Create `feature/<issue-number>-<slug>` (or `fix/<issue-number>-<slug>`) from the latest `main`. Never commit gameplay directly to `main`.
- Implement acceptance criteria and targeted tests; open a PR against `main`, reference the Issue with `Closes #<number>`, include actual test evidence and limitations. **Never merge your own PR, bypass checks or close a story as Done before the owner merges after testing.** Do not create or merge PRs during the story-generation-only task.
- GitHub Issue/PR is the operational status record: Backlog → Ready (owner approval) → In Progress → In Review → Done (after merge). Keep BMAD sprint tracking consistent with actual state; do not assert sync was automated if it was manual.

## Token-efficient engineering
- One story per implementation session. Read `AGENTS.md`, that Issue, its specific BMAD story, and only task-relevant source/docs. Do not repeatedly load the entire PRD/architecture or regenerate accepted documents.
- Unity code under `Assets/Game/` once a real Unity project exists; backend under `backend/`. Keep simulation and rendering, run saves and account state, earned ownership and paid entitlements separated.
- Never fabricate a working Unity project, installed SDK, CI checks or passing tests. State which commands/devices were actually tested. Add focused tests for damage, wave state, saves, rewards, unlocks and billing as appropriate.
- No secrets, service accounts, keystores, live receipts, personal data or Unity-generated `Library/`, `Temp/`, `Obj/` and `Build/` directories in Git.
- Report concisely: changed files, tests run and results, blockers, PR URL. Never reduce necessary security or acceptance checks to save tokens.

## Change control
- If a story conflicts with reviewed product or technical decisions, raise it before changing scope. Approved decisions update affected docs and, where significant, an ADR in `docs/decisions/`.
- Follow `docs/development/testing-strategy.md`; do not claim a green GitHub status check unless a workflow actually exists and has run.
