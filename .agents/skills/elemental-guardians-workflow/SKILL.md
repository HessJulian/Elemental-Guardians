---
name: elemental-guardians-workflow
description: 'Single entry point for Elemental Guardians work in Codex: plan with BMAD, create epics/stories and GitHub Issues, implement one approved issue, or review a PR without manually invoking BMAD persona agents. Use for project planning, stories, implementation, reviews, or requests such as "what next"; not for unrelated questions.'
---

# Elemental Guardians — project workflow router

This skill is a **Codex orchestration layer**, not a replacement for installed BMAD skills. The **primary Codex session** owns the user conversation, official BMAD step-file execution, artifact writing, GitHub operations and final report. Start optional Codex role subagents from `.codex/config.toml` **only for bounded independent subtasks**; they provide advice/review and do not silently advance official BMAD steps. The user need not invoke Mary, John, Sally, Winston or Amelia by hand.

## Determine intent and live state

1. Follow root `AGENTS.md`. Route planning, epics/stories, approved-story publication, implementation, review and next-step requests to the corresponding **installed** official skill. Use `bmad-help` when the next skill/prerequisite is unclear.
2. Inspect current target `main`, relevant code/tests, GitHub Issue/PR state and completion markers in actual BMAD output. Do not infer *implementation status* from design docs, README, old chat or simply the presence of a draft artifact.
3. Read only the documents relevant to the current task. Follow `docs/development/workflow.md` and `docs/development/definition-of-done.md`. An unmerged PR is not on `main`.

## Product discovery: reuse committed decisions, do not interview from zero

- For **Elemental Guardians**, the owner's existing product input is already committed in `docs/game-design.md`, `docs/architecture.md`, `docs/data-contracts.md`, `docs/mvp-roadmap.md` and approved `docs/decisions/`. When a BMAD step asks for a free-form **brain dump**, initial project description, additional reference files, or broad requirements recap, **first ingest those relevant files** as the user's supplied input. Do not ask the user to repeat their contents, nor ask for a new unfiltered brain dump by default. Cite relevant file locations in the resulting official BMAD artifact rather than copying the entire docs tree into every chat reply.
- Distinguish **fixed product requirements**, **proposed technical designs** and **unverified assumptions** from those files. Translate the approved requirements into the official PRD/UX/architecture outputs as the installed BMAD workflows prescribe. Existing `docs/architecture.md` is design input and is *not* an automatically approved BMAD architecture artifact; similarly UI requirements in a game design are *not* automatically an approved BMAD UX contract.
- If discovery finds a decision genuinely necessary to continue that these files do not answer, first state the exact unresolved point, relevant file/section and the effect on the MVP; ask a **narrow, actionable question**, preferably with a safe provisional default when the official step permits it. Collect related questions once, not repeated generic requests for context. Do not invent product decisions or mark unapproved artifacts approved.
- If the **installed official BMAD step explicitly requires a user response or menu choice**, follow it and pause for that response. The already-present documents may be supplied as the discovery *content*, but never forge a literal user reply such as 'Keine Ergänzungen' or auto-select a Continue/approval gate. Once the owner answers, resume the *existing* draft and its recorded step state; do not create a second PRD or restart completed steps.
- When a PRD draft is already resumable in the developer's working copy, resume that exact draft **at its current step** after the owner responds; inspect the configured BMAD output location. A local-only draft may not exist on GitHub: do not infer its absence locally from the remote repository or rewrite it remotely.

## Planning: route, do not invent BMAD

- Existing reviewed game design and architecture docs in `docs/` are inputs, not substitutes for BMAD's required official artifacts. Use `bmad-help` / `_bmad/_config/bmad-help.csv` to resolve the *actual* prerequisite and workflow skill names for this installation. Never invent a skill name, change upstream `_bmad/` internals or skip an official prerequisite.
- For a request to create stories, determine whether the required PRD, architecture and applicable UX artifacts have been completed **and approved**. If not, run the respective official prerequisite workflow(s) in order; only then run installed `bmad-create-epics-and-stories` following its complete steps. The primary session executes the step-file sequence and writes the official artifacts in the configured location.
- **BMAD user-interaction gates remain binding.** When a workflow asks the owner to choose an option, approve a document or continue, pause and ask; do not simulate approval or force unattended advancement. Resume the current step after the answer.
- Owner approves story decomposition before publishing implementation Issues; check existing Issues by BMAD story ID/reference to avoid duplicates. GitHub allocates Issue numbers.

## Implementation / review

- One **owner-approved Ready** Issue per implementation task. Confirm linked story, dependencies and actual `main` state; follow the installed official BMAD implementation skill if required and preserve its interaction gates. Branch from latest `main`, implement acceptance criteria with tests and create PR; **never merge** or assert Done before owner merge.
- For review, inspect PR diff, related story and directly affected code/tests. For billing/progression security, request an architecture/security review where warranted rather than optimizing away required checks.

## Role delegation and token policy

- **Do not spawn all BMAD personas as a committee.** The primary session orchestrates. Spawn a configured specialist only for an independently useful bounded subtask: `bmad_analyst` for a specific requirements gap; `bmad_pm` for story scope/acceptance; `bmad_ux` for mobile UX/accessibility; `bmad_architect` for consequential architecture/identity/billing; `bmad_developer` for approved bounded coding; `repo_explorer` for focused inspection; `rubric_checker` for independent acceptance-evidence checks.
- Spawn by configured role name without overriding its model/reasoning; `.codex/agents/*.toml` defines them. A BMAD skill in the primary session does **not** automatically use the model of the similarly named Codex role. Do not claim a role ran unless it was spawned.
- Prefer none or one targeted role. Independent read-only roles may run concurrently if they do not compete over artifacts/BMAD step state. Primary session integrates findings and performs edits. Prefer deterministic checks before optional agent review.

## Final output

Report the actual selected workflow/step, written artifacts or Issue/PR URL, tests actually run, genuine unanswered BMAD approval gates and precise next action. Do not duplicate progress registers or request an already supplied general product brief.
