---
name: elemental-guardians-workflow
description: 'Single entry point for Elemental Guardians work in Codex: plan with BMAD, create epics/stories and GitHub Issues, implement one approved issue, or review a PR without manually invoking BMAD persona agents. Use for project planning, stories, implementation, reviews, or requests such as "what next"; not for unrelated questions.'
---

# Elemental Guardians — project workflow router

This skill is a **Codex orchestration layer**, not a replacement for installed BMAD skills. The **primary Codex session** owns the user conversation, official BMAD step-file execution, artifact writing, GitHub operations and final report. Start optional Codex role subagents from `.codex/config.toml` **only for bounded independent subtasks**; they provide advice/review and do not silently advance official BMAD steps. No user needs to invoke Mary, John, Sally, Winston or Amelia by hand.

## Determine intent and live state

1. Follow root `AGENTS.md`. Determine whether the request means planning, generating epics/stories, publishing approved stories as Issues, implementing an owner-approved Issue, reviewing a PR, or asking what to do next. If intent is truly ambiguous, use installed `bmad-help`; otherwise choose the relevant installed official skill directly.
2. Inspect the current branch and target `main`, relevant code/config/tests, GitHub Issue/PR state and the **completion markers** of the actual BMAD artifacts in the installed output location. Never derive *current implementation status* from README, roadmap, or previous chat. An existing artifact alone does not prove a BMAD workflow is complete.
3. Read only the documentation necessary for that phase or Issue. Follow `docs/development/workflow.md` and `docs/development/definition-of-done.md` once available on the target branch. A PR not yet merged to `main` is not implemented on `main`.

## Planning: route, do not invent BMAD

- Existing reviewed game design and architecture docs in `docs/` are **input**, not substitutes for BMAD's required official artifacts. Use installed `bmad-help` / `_bmad/_config/bmad-help.csv` to resolve the *actual* prerequisite and workflow skill names for this installation. Never invent a skill name, change upstream `_bmad/` internals or skip an official prerequisite.
- For a request to create stories, first determine whether the required PRD/architecture approvals exist. If not, run the appropriate **official** prerequisite workflow(s) in order; then run installed `bmad-create-epics-and-stories` following its complete step files. For an entire multi-step workflow, the primary session acts as executor and writes the official artifacts in the configured location.
- **BMAD user-interaction gates remain binding.** When an installed workflow asks the owner to choose an option, approve a document or continue, pause and ask; do not simulate approval, invent a response, or force unattended advancement. Once the user replies, resume the current step rather than restarting planning.
- Owner approves the decomposition before publishing implementation Issues; check for existing Issues by BMAD story ID/reference to avoid duplicates. Issue numbers are assigned by GitHub, not guessed.

## Implementation / review

- One **owner-approved Ready** GitHub Issue per implementation task. Confirm linked story, dependencies and actual `main` state; follow the installed official BMAD implementation skill if required for this work and preserve its interaction gates. Branch from latest `main`, implement scope + tests, create a PR with actual results; **never merge** or assert Done before the owner merges.
- For a code-review request inspect only the PR diff, related story and directly affected code/tests; select the installed official review skill if it fits. For security-sensitive purchase, fragments and entitlement changes, request an architecture/security review rather than optimizing away necessary validation.

## Role delegation and token policy

- **Do not spawn all BMAD personas as a committee.** The primary Codex session is the workflow orchestrator. Spawn a configured specialist only if its independent task materially helps: `bmad_analyst` for a specific requirements gap; `bmad_pm` for story boundaries/acceptance; `bmad_ux` for mobile interaction/accessibility; `bmad_architect` for consequential architecture, identity, save integrity or billing security; `bmad_developer` for an approved bounded code task when delegated implementation is useful; `repo_explorer` for focused read-only inspection; `rubric_checker` for an independent acceptance-evidence check.
- Spawn by the **configured role name**, without overriding its model or reasoning effort; the role's `.codex/agents/*.toml` defines those. Do not claim that executing a BMAD skill automatically adopts the model of an identically named Codex role; it does not. Do not claim a role ran unless the Codex runtime actually spawned it.
- Prefer one targeted role or none. Independent roles may run concurrently only when they do not compete over artifact editing or BMAD step state. Read-only roles return concise findings; the primary executor integrates them and performs any artifact edits. Run cheap deterministic checks before commissioning additional review.

## Final output

Report only the selected workflow/real executed step, created/updated artifacts or Issue/PR URL, tests actually run, unanswered BMAD gates, and exact next owner action. No duplicated progress registers or speculative success claims.
