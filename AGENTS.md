# Agent instructions — Elemental Guardians

Applies repository-wide unless a closer `AGENTS.md` provides additional guidance. Official BMAD files in `_bmad/` and installed `bmad-*` skills in `.agents/skills/` are installer-managed: do not edit them to customize this project.

## Default entry point
For Elemental Guardians planning, epic/story generation, GitHub Issue publication, implementation, or PR review, use the **project-owned** `.agents/skills/elemental-guardians-workflow/SKILL.md` as the single routing guide. Select the relevant **installed official BMAD workflow** based on task and completed prerequisite artifacts. Do not require the owner to manually invoke Mary, John, Sally, Winston, or Amelia. The primary Codex session executes the official workflow; configured Codex subagents are optional bounded specialists, not replacements for BMAD step files. Honor all BMAD menus, user approvals and continuation gates; do not simulate an owner's responses.

`.codex/config.toml` is Codex runtime configuration, **not** a BMAD workflow-customization file. BMAD-owned customization belongs in installer-supported `_bmad/custom/`; project routing lives in the project skill above. Do not assume executing a BMAD skill automatically runs under a separately configured Codex subagent model. Delegate explicitly only when useful and actually supported by the running Codex environment.

## Product and context
- Product requirements: `docs/game-design.md`; design inputs: `docs/architecture.md` and `docs/data-contracts.md`. Read task-relevant sections. These documents describe intended behavior and decisions, **not whether a feature has been implemented**.
- Android landscape single-player, one actively fighting hero per run, 20 fixed waves, 10–15-minute target; Kael free; Lyra/Varek earned with fragments or purchased individually and intentionally stronger. Four disciplines, 11 planned towers.
- Original art/code/maps/names/UI/sounds only; never copy Warcraft III or Element TD assets, maps, source or distinctive presentation.
- Combat locally simulated; backend owns durable progression, fragments and purchase entitlements. Validate purchases server-side; rewards/unlocks idempotent. Client-reported results alone do not prove play.

## Current state and source of truth
- **Never infer implementation status from README, docs, roadmaps, BMAD planning files or previous conversations.** Inspect the actual target-branch code/config/tests, relevant GitHub Issues/PRs and actual checks at task time. An open PR is not integrated into `main`.
- Current code/config is authority for integrated behavior; GitHub Issues and PRs for operational work state; real test logs/checks for verification. Inspect BMAD output completion markers separately to determine BMAD planning progress.
- Do not maintain duplicate progress lists or embed ephemeral status in permanent docs. Official BMAD sprint tracking, if required, is a derived view reconciled against GitHub, not an independent source of operational truth.

## Development workflow and safety
- `docs/development/workflow.md` and `docs/development/definition-of-done.md` define the project Issue/PR process. BMAD-generated approved story is the implementation specification; GitHub Issue is its operational ticket. Check duplicates before publishing Issues.
- Implement only one owner-approved Ready Issue per coding session, from latest `main` on `feature/<issue-number>-<slug>` (or `fix/<issue-number>-<slug>`). Tests and acceptance criteria required. Open a PR referencing the Issue and actual test results. **Do not merge, bypass review, mark Done pre-merge or create an implementation PR during a planning-only request.**
- Keep Unity code under `Assets/Game/` once a real project exists; backend under `backend/`. Never fabricate projects, tooling, passing tests or CI. Do not commit credentials, signing keys, live receipts, personal data or Unity-generated build caches.
- When approved decisions change, update relevant design documents and an ADR for significant changes; resolve contradictions before implementing.
- Keep context focused to current Issue, its BMAD story and affected files. Delegate specialists only when they add value, using `.codex/agents/*.toml` role configuration without guessing runtime/model support. Concise closing report: changed files, tests actually run, blockers and PR link.
