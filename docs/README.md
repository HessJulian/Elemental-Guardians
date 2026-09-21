# Documentation index / source of truth

| Document | Purpose |
| --- | --- |
| [`game-design.md`](game-design.md) | Approved gameplay, heroes, elements, economy and MVP rules |
| [`architecture.md`](architecture.md) | Proposed client/backend architecture and trust boundaries |
| [`data-contracts.md`](data-contracts.md) | Domain models, API contract and persistence invariants |
| [`mvp-roadmap.md`](mvp-roadmap.md) | Vertical slice, milestones and acceptance criteria |
| [`development/bmad-codex.md`](development/bmad-codex.md) | BMAD installation/status and installed Codex workflow |
| [`development/workflow.md`](development/workflow.md) | BMAD story → GitHub Issue → Codex PR → human merge |
| [`development/definition-of-done.md`](development/definition-of-done.md) | Explicit Ready and Done gates |
| [`development/testing-strategy.md`](development/testing-strategy.md) | Tests and truthful PR verification by change type |
| [`decisions/0001-engine-and-authority.md`](decisions/0001-engine-and-authority.md) | First proposed architecture decision |

**Status:** Reviewed product baseline exists; technical choices require BMAD architecture validation. BMAD 6.12.0 (`core` + `bmm`, Codex integration) is installed in the repository; no official planning artifacts or implementation Stories have yet been approved. No playable Unity project, deployed backend, enforced branch protection or game CI checks exist yet. Prices, balance and duration remain hypotheses.

**Handoff:** Run installed `bmad-help`, complete prerequisites, then use `bmad-create-epics-and-stories`; review the resulting Stories before creating GitHub Issues. New Issues begin Backlog, Codex only works on owner-approved Ready Issues, and only the owner merges PRs after testing.

**Language:** Project docs are in English for tool portability; these workflow notes are in German. End-user localization remains undecided.
