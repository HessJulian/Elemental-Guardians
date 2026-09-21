# Elemental Guardians

Independent Android elemental tower-defense game with one actively fighting hero per run. Product requirements and intended architecture are in [`docs/`](docs/README.md).

## Product at a glance

- Android landscape, single-player, fixed route and 20 deterministic waves per run (target: 10–15 minutes).
- Four original disciplines: Ember (Glut), Tide (Flut), Ore (Erz), Pulse (Impuls); 11 planned towers, including neutral and two-element combinations.
- Exactly one actively fighting hero per run. Kael is free; Lyra and Varek are earnable via fragments or individually purchasable; advanced heroes deliberately provide gameplay advantages.
- Local combat simulation and resumable runs; account-bound progression and purchase entitlements managed server-side.
- Original art, names, maps, sound, UI, code, balancing and element rules; never import Warcraft III or Element TD assets, code, maps or distinctive presentation.

## One Codex entry point

Open Codex at the repository root and describe your task normally: e.g. **"Plane die MVP-Stories"**, **"Erstelle die freigegebenen GitHub Issues"** or **"Implementiere das freigegebene Issue #N"**. [`AGENTS.md`](AGENTS.md) routes project work through the project-owned [Elemental Guardians workflow skill](.agents/skills/elemental-guardians-workflow/SKILL.md). It selects installed official BMAD workflows, optionally delegates bounded consultation to configured Codex roles, and retains all required BMAD approval/continuation gates. You do not need to invoke individual BMAD personas manually.

The roles and their respective models are configured in [`.codex/config.toml`](.codex/config.toml) and [`.codex/agents/`](.codex/agents/). `_bmad/` is the official BMAD installation; `_bmad/custom/` is its supported team customization location. `.codex/config.toml` configures **Codex**, not BMAD workflow steps. See [`docs/development/bmad-codex.md`](docs/development/bmad-codex.md).

Approved BMAD Story → GitHub Issue → Codex feature branch/PR → **owner testing and merge**. See [`docs/development/workflow.md`](docs/development/workflow.md).

## Where to find the current state

**This README intentionally contains no implementation status, feature completion list or next-task snapshot.** Inspect code/configuration on the current target branch, GitHub [Issues](https://github.com/HessJulian/Elemental-Guardians/issues), [Pull Requests](https://github.com/HessJulian/Elemental-Guardians/pulls) and real checks on the relevant revision. An open PR is not part of `main`. Planning documents and old agent conversations do not report live implementation status.

Use Unity Hub to create or open the real Unity project when required. Never commit credentials, service accounts, signing keys or live billing tokens.
