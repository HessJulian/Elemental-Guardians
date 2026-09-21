# BMAD + Codex — installation and workflow

## Check the installation instead of trusting a status snapshot

- Inspect the current checkout for the official BMAD configuration under `_bmad/` and the installed Codex skills under `.agents/skills/`. Determine the actual version/modules and configured output paths from those files and the installed tooling; never rely on a dated statement in this document.
- If BMAD or its Codex integration is actually missing or broken, run the **official** installer from the repository root (`npx bmad-method install`), select the appropriate BMM module and Codex integration, check its output and restart Codex. Do not hand-edit installer-managed BMAD internals or reinstall just because a README describes an earlier state.
- Locate BMAD-generated PRD, architecture, epics and implementation stories using the installed configuration. Their presence or approval must be checked in the current checkout and linked GitHub Issues/PRs; do not assume either from this guide. Use the configured output directory rather than inventing artifact paths.

## Planning handoff

1. Read `AGENTS.md` and `docs/development/workflow.md`; use only task-relevant product/architecture sections from `docs/`. Invoke the installed `bmad-help` skill to determine the required official planning/validation sequence.
2. Existing design documents are baseline inputs, **not** evidence of completed BMAD workflows or implemented gameplay. Check which planning artifacts actually exist and which have been approved, then execute only the missing official stages without skipping prerequisites.
3. When prerequisites are fulfilled, use the installed `bmad-create-epics-and-stories` skill to produce and validate story decomposition. Follow its sequential workflow and user approval gates.
4. Before publishing Stories as GitHub Issues, search existing Issues by BMAD Story ID and linked file to prevent duplicates. The owner reviews and explicitly makes an Issue Ready. See `docs/development/workflow.md` for implementation and owner-merge rules.
5. For each subsequent task, determine current feature state from the latest `main` code/configuration and the relevant Issue/PR, not from this installation guide or prior conversations.

## Official references

- https://docs.bmad-method.org/start/install-bmad/
- https://developers.openai.com/codex/guides/agents-md/
