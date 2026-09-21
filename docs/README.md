# Documentation index — intended behavior and decisions

| Document | Purpose |
| --- | --- |
| [`game-design.md`](game-design.md) | Reviewed gameplay requirements, heroes, elements and economy |
| [`architecture.md`](architecture.md) | Intended client/backend architecture and trust boundaries |
| [`data-contracts.md`](data-contracts.md) | Domain models, API contracts and persistence invariants |
| [`mvp-roadmap.md`](mvp-roadmap.md) | Intended milestones and acceptance criteria, not a completion checklist |
| [`development/bmad-codex.md`](development/bmad-codex.md) | BMAD/Codex installation guidance and planning handoff |
| [`development/workflow.md`](development/workflow.md) | BMAD Story → GitHub Issue → Codex PR → owner merge; authoritative live-status rules |
| [`development/definition-of-done.md`](development/definition-of-done.md) | Ready and Done gates |
| [`development/testing-strategy.md`](development/testing-strategy.md) | Test approach and truthful PR verification |
| [`decisions/0001-engine-and-authority.md`](decisions/0001-engine-and-authority.md) | Architecture decision record |

**This directory is not a progress dashboard.** Its documents describe target behavior, designs and agreed decisions. Do not add claims such as "not yet implemented", "BMAD planning not yet approved", "Unity installed", "CI available" or "next issue is ..." here: such statements become stale. Determine current implementation from the latest `main` code/configuration; work status and approval from [Issues](https://github.com/HessJulian/Elemental-Guardians/issues) and [PRs](https://github.com/HessJulian/Elemental-Guardians/pulls); test status from actual checks/reports on the relevant revision.

**Change control:** Approved requirement/design changes update the affected document and, when significant, an ADR. Routine work/status transitions update GitHub, not this index. Official BMAD sprint tracking, when required, is a derived view and must be reconciled against GitHub before making decisions.
