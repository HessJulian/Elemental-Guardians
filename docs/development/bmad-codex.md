# BMAD + Codex — installation and workflow

This repo intentionally does **not** contain a hand-made BMAD installation. The official installer must create its own files and Codex-compatible skills; a Markdown file named after an agent is not a substitute for an installed BMAD skill.

## Installation: status and recovery

- Verified in repository on 2026-09-21: official BMAD 6.12.0 is installed (`core` + `bmm`) with Codex skills under `.agents/skills/`. Do **not** reinstall it merely to create project-specific Issue templates.
- For a missing/broken local installation, run `npx bmad-method install` from repository root with the BMM module and Codex integration, check installer output, and restart Codex. Do not hand-edit generated `_bmad/` or `.agents/skills/bmad-*` internals.
- The installer-managed output location governs generated PRD/architecture/epics/story files (normally `_bmad-output/`); do not invent output files or claim a planning artifact is already approved.

## Starting BMAD planning

1. Read root `AGENTS.md`, `docs/development/workflow.md`, and only the relevant product docs. Invoke installed `bmad-help` to determine the required planning/validation sequence for the installed version.
2. Existing `docs/game-design.md`, `docs/architecture.md`, `docs/data-contracts.md`, `docs/mvp-roadmap.md` are inputs, not automatically an approved BMAD PRD or BMAD architecture artifact.
3. Once official prerequisites have been satisfied, invoke installed `bmad-create-epics-and-stories` for Epic/Story decomposition. Follow its step-by-step interaction and validation; do not shortcut or overwrite earlier approvals.
4. Owner reviews decomposition before Issues are marked Ready; publish each reviewed implementation Story as a GitHub Issue according to `docs/development/workflow.md`.
5. First implementation milestone is the five-wave Unity vertical slice; no premature billing backend before the basic combat loop is playable.

## Official references

- https://docs.bmad-method.org/start/install-bmad/
- https://developers.openai.com/codex/guides/agents-md/
