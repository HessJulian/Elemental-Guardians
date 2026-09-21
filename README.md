# Elemental Guardians

Independent Android elemental tower-defense game with one actively fighting hero per run. Product requirements and intended architecture are documented in [`docs/`](docs/README.md).

## Product at a glance

- Android landscape, single-player, fixed route and 20 deterministic waves per run (target: 10–15 minutes).
- Four original disciplines: Ember (Glut), Tide (Flut), Ore (Erz), Pulse (Impuls); 11 planned towers including neutral and two-element towers.
- Exactly one actively fighting hero per run. Kael is free; Lyra and Varek are earnable via fragments or individually purchasable. Advanced heroes intentionally provide gameplay advantages.
- Local combat simulation and resumable runs; account-bound progression and purchase entitlements managed server-side.
- Original artwork, names, map, sound, UI, code, balancing and element rules. Do not import or recreate Warcraft III or Element TD assets, code, maps, distinctive artwork, or branding.

## Development

- Codex starts at [`AGENTS.md`](AGENTS.md); process: [`docs/development/workflow.md`](docs/development/workflow.md).
- Use the installed official BMAD skills for planning and Story creation. Approved BMAD Story → GitHub Issue → Codex feature branch/PR → owner testing and merge.
- The intended initial gameplay milestone is a Unity vertical slice: one map, one basic tower, Kael, five fixed waves, combat loop and restart. See [`docs/mvp-roadmap.md`](docs/mvp-roadmap.md) for intended milestones, **not a live delivery tracker**.

## Where to find the current state

**This README intentionally contains no implementation status, completed-feature checklist or next-task snapshot.** For the actual delivered functionality inspect code and configuration on the latest `main`; for open and completed work consult [GitHub Issues](https://github.com/HessJulian/Elemental-Guardians/issues) and [Pull Requests](https://github.com/HessJulian/Elemental-Guardians/pulls). Read CI/test results on the relevant commit. An open PR is not yet implemented on `main`; do not infer current state from planning documents, comments or previous Codex conversations.

Use Unity Hub to generate or open the actual Unity project when appropriate; treat `Assets/`, `Packages/` and `ProjectSettings/` as engine-managed structure, not proof that a playable game exists. Never store credentials, service accounts, signing keys or live billing tokens in Git.
