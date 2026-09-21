# Elemental Guardians

Independent Android elemental tower-defense game with one actively controlled hero per run. The game design and implementation plan live in [`docs/`](docs/README.md).

> Status: **pre-production**. This repository contains an agent-ready project scaffold and design documents; no playable Unity project, backend, BMAD installation, or billing integration exists yet.

## Product at a glance

- Android landscape, single-player, fixed route and 20 deterministic waves per run (target: 10–15 minutes).
- Four original disciplines: Ember (Glut), Tide (Flut), Ore (Erz), Pulse (Impuls); 11 planned towers including neutral and two-element towers.
- Exactly one actively controlled hero per run. Kael is free; Lyra and Varek are unlockable via earned fragments or individually purchasable. Advanced heroes intentionally provide gameplay advantages.
- Local combat simulation and resumable runs; account-bound progression and purchase entitlements managed server-side.
- Original artwork, names, map, sound, UI, code, balancing and element rules. Do not import or recreate Warcraft III or Element TD assets, code, maps, distinctive artwork, or branding.

## For Codex and BMAD

1. Read [`AGENTS.md`](AGENTS.md), then [`docs/README.md`](docs/README.md) and the relevant source-of-truth documents.
2. Install **official BMAD** in this repository using `npx bmad-method install`, select the BMM module and the supported Codex tool integration from the installer. See [`docs/development/bmad-codex.md`](docs/development/bmad-codex.md). Do not manually invent `_bmad/` or BMAD agents/skills.
3. Run the installed `bmad-help` skill in Codex to select the appropriate planning workflow. Store generated planning/implementation artifacts in the installer-configured `_bmad-output/` path; keep reviewed product decisions in `docs/`.
4. Build the first playable Unity vertical slice before implementing a store: one map, one basic tower, Kael, five fixed waves, combat loop and restart.

## Intended top-level structure

```text
AGENTS.md                    Codex repository instructions
.bmad/                      project-specific BMAD notes (not a fake BMAD installation)
_bmad/                      created by the official installer, not pre-populated here
_bmad-output/               BMAD-generated artifacts (once installed)
docs/                       reviewed product and engineering sources of truth
Assets/                     Unity project assets and C# code (placeholder only)
Packages/                   Unity package manifest (created by Unity)
ProjectSettings/            Unity-generated project settings (created by Unity)
backend/                    account, progression and billing API (placeholder only)
.github/                    PR template and collaboration conventions
```

## Status and next step

No engine-generated metadata or package versions are fabricated in this scaffold. Create the Unity project with a supported Unity LTS release, commit the resulting `Assets/`, `Packages/`, `ProjectSettings/`, and add the corresponding `Assets/AGENTS.md` guidance before gameplay implementation. Never store credentials, service accounts, signing keys or live billing tokens in Git.
