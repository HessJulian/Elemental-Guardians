# BMAD + Codex: one project entry point

## Directory ownership (no duplicate BMAD installations)

| Location | Owner / purpose | What to change |
| --- | --- | --- |
| `_bmad/` | Official installer-generated BMAD engine, module content and scripts | **Do not hand-edit installer-managed internals.** Update with official installer. |
| `_bmad/custom/` | Supported team-level BMAD config and skill customization | Use only the documented overrides supported by the installed BMAD release; do not edit upstream skill steps. |
| `.agents/skills/bmad-*` | Official BMAD skills exposed to Codex | Installed/generated; do not edit. |
| `.agents/skills/elemental-guardians-workflow/` | **Project-owned** Codex entry-point/router | Edit `SKILL.md` to route work to actual installed official skills. |
| `.codex/config.toml`, `.codex/agents/*.toml` | Codex runtime, optional subagents, per-role models, reasoning and sandboxes | Tune role profiles and delegation limits; **these files are not BMAD workflow settings**. |
| `_bmad-output/` (resolved from installed config) | BMAD-generated planning and implementation artifacts | Preserve official workflow's artifacts, completion markers and interaction gates. |

The former `.bmad/README.md` was only a duplicate project note, not a second installation. Avoid creating an additional directory for the same purpose. Use this guide and `AGENTS.md` for project rules, and `_bmad/custom/` only when a supported BMAD override is genuinely required.

## Starting work: owner needs no persona commands

Start Codex at repository root after pulling the merged workflow PR. For project work simply ask, for example, **"Erstelle die Epics und Stories für das MVP"** or **"Implementiere das freigegebene Issue #N"**. Codex follows root `AGENTS.md` and the project-owned `elemental-guardians-workflow` skill to select the installed official BMAD step workflow, its prerequisites and any optional specialist role. Manual `bmad-agent-pm`, `bmad-agent-architect` or equivalent invocation is not necessary.

When prerequisites or explicit owner approval are required, the router must **stop at the official BMAD interaction gate** rather than silently advancing. The router is not a fully unattended batch runner.

## How model routing really works

A BMAD skill or agent *persona* executed in the current Codex session uses that session's model. Merely configuring `bmad_pm` in `.codex/config.toml` does not switch the current session to its model. To use role-specific models, the primary Codex session must **actually delegate a bounded task** to a configured Codex subagent; its `.codex/agents/*.toml` sets model and reasoning effort (provided that model and multi-agent support are available in the local Codex runtime/account). The main session integrates read-only findings and executes/writes official BMAD artifacts.

The router requests **zero or one useful specialist by default**, not every persona. Suggested profiles already defined in `.codex/agents/`: analyst/PM/UX -> Terra medium; architect -> Sol high when needed; developer -> Sol medium for an approved code task; repository explorer -> Luna low; rubric checker -> Luna medium. Runtime availability of these model IDs and actual delegation must be verified locally; configuration alone does not prove successful execution or token savings.

Avoid delegating the interactive BMAD step-file state to competing subagents: official prerequisites, sequential steps and user approval remain the responsibility of the primary session. Do not load an entire PRD and architecture in every coding session; limit context to the live Issue, linked Story and affected files. Count total tokens and retries, not just shortened agent responses.

## Installation and source-of-truth verification

Inspect the actual checkout for `_bmad/`, `_bmad/_config/bmad-help.csv`, `.agents/skills/bmad-help/SKILL.md` and the required installed BMAD skill; resolve the output folder from installed config. Use `bmad-help` where stage/prerequisite selection is unclear. The presence of an artifact does not by itself prove it was approved/completed; inspect its completion markers and GitHub approvals. Never take current development status from this document.

If BMAD or Codex skill integration is actually missing/broken, use the **official installer** (`npx bmad-method install`) for the relevant modules and integration rather than recreating upstream files. Recheck generated skills and Codex configuration after installer updates; update only the project-owned router and supported custom overrides.

## Official documentation

- https://docs.bmad-method.org/start/install-bmad/
- https://developers.openai.com/codex/guides/agents-md/
- https://developers.openai.com/codex/multi-agent/
