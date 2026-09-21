# Agent instructions — Elemental Guardians

Applies to the repository root and descendants unless a nearer `AGENTS.md` supplies more specific instructions. Codex loads this standard filename automatically; BMAD's installer-managed agents/skills are separate.

## Mission and sources of truth
- First read `docs/README.md`, `docs/game-design.md`, `docs/architecture.md`, `docs/mvp-roadmap.md`, and the relevant story in the **official BMAD-generated** implementation artifacts.
- The reviewed product decisions in `docs/` are binding. If a story conflicts with them, flag the discrepancy; do not silently change the product. Record approved changes with an ADR in `docs/decisions/` and update affected docs.
- The repo is in PRE-PRODUCTION until Unity and BMAD are actually installed. Do not claim that scaffolding placeholders are runnable.
- Do not imitate or copy Warcraft III / Element TD assets, source, maps, UI, names, artwork, sounds, or distinctive presentation. Create original expression and escalate IP uncertainty for review.

## BMAD + Codex workflow
1. If BMAD is not installed, follow `docs/development/bmad-codex.md` and use `npx bmad-method install` in the repository root; select the official BMM module and supported Codex integration. Do not handcraft `_bmad/`, `.agents/skills/bmad-*`, or BMAD internal config.
2. Invoke the installed `bmad-help` skill to select the next official planning/implementation workflow; use its generated artifacts and story acceptance criteria before coding.
3. Work one approved, independently testable story at a time. Examine existing files first, write or update tests, implement the minimum change, run relevant checks, update docs and report changes and remaining risks.
4. Never mark a story done without evidence of passing applicable tests. If Unity, credentials, Android SDK or billing sandbox is unavailable, say which verification was not performed.
5. Prefer small PRs, meaningful commits and traceability from requirements → story → code/tests. Do not commit generated credentials, account files, keystores, live purchase tokens or personal information.

## Invariants
- Android landscape single-player; 20 **fixed** waves per difficulty/map; target 10–15 minutes; exactly one actively fighting hero per run; Kael starts unlocked; Lyra and Varek unlock via earned fragments or individual one-time purchases; advanced heroes deliberately grant gameplay advantage.
- Four disciplines (Ember/Glut, Tide/Flut, Ore/Erz, Pulse/Impuls); 11 planned tower types. Combat is local; durable currency/ownership and purchase verification are server authoritative.
- Do not treat client-reported wave completion as cryptographic proof of play. Never grant entitlements from a client receipt alone; verify purchase and transaction state server-side. Ensure idempotent rewards/unlocks.

## Engineering conventions
- Unity gameplay C# under `Assets/Game/` once a genuine Unity project is generated; prefer data-driven definitions and pure domain logic where practical. Separate simulation from rendering, persistent profile from resumable run, and purchased entitlements from earned hero ownership.
- The backend stays in `backend/`; document API and schema changes. No real store products, API keys, Firebase project IDs or Unity package versions are assumed by this scaffold.
- Add targeted tests for changes to damage, wave progression, rewards, unlocks, save/load and purchase state. Do not fabricate test results or commit Unity-generated `Library/`, `Temp/`, `Obj/`, `Build/` directories.

## Definition of done
Acceptance criteria met; tests added/updated and executed where possible; no unreviewed scope changes; public documentation updated; security/privacy and mobile performance considered; clearly report unverified steps.


## Context and token efficiency

- Treat docs/ as the product source of truth.
- Read only the documents relevant to the current task.
- Do not read the entire documentation directory.
- Do not repeat existing design decisions in chat.
- Implement one approved story at a time.
- Prefer targeted file inspection over repository-wide searches.
- Do not regenerate existing planning documents unless requirements changed.
- Run targeted tests before broader validation.
- Keep responses concise: changes, tests, blockers and next steps.
- Do not skip required security or acceptance checks to save tokens.
