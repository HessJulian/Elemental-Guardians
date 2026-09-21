# Architecture proposal — review through BMAD before implementation

## Proposed stack
Unity LTS and C# Android landscape game; isometric-style 2D sprites. Confirm the installed supported editor and plugin versions before writing package manifests. Firebase Authentication + Cloud Run REST service + Firestore for account-bound progression and verified entitlements. Unity IAP / Google Play Billing for non-consumable hero products; server verifies using Google Play Developer API. This stack is a proposal, not deployed infrastructure.

## Trust and runtime boundaries
- **Device / Unity:** authoritative for immediate local combat simulation, presentation and resumable mid-run snapshot; never authoritative for money or permanent unlock ownership.
- **Backend:** sole writer of profile XP, fragment balance, hero unlock/mastery, reward ledger and verified purchase grants; database transactions for spend+unlock, idempotency keys for reward completion.
- **Google Play:** payment lifecycle; never grant from client callbacks alone. Verify completed purchase server-side, confirm/acknowledge appropriately, handle pending/canceled/refunded purchases and restore owned items. Use a separate earned and purchased entitlement basis so refunding one does not remove an independently earned hero.
- **Known limitation:** a local combat client can be modified; server-side plausibility checks on run time, progression and rewards are not proof of legitimate play. No competitive cash/reward leaderboards until stronger validation is designed.

## Client modules
`Core` (state machine, simulation clock), `Map/Navigation` (enemy fixed waypoints; hero walkability), `Enemies/Waves`, `Towers/Targeting/Projectiles`, `Combat/StatusEffects/Resonance`, `Elements`, `Heroes/Abilities`, `RunEconomy`, `UI`, `Persistence` (local snapshot), `Progression/Commerce` (API integration). Use ScriptableObjects or versioned data assets for static heroes, towers, waves; runtime mutable state must be separate. Prefer deterministic fixed-step combat simulation (initial target 30Hz) and object pooling; render frame rate independent of combat time. Deterministic *wave definitions* do not imply perfect cross-device replay determinism.

## Save and resume
Atomic versioned local run snapshots at wave boundaries and when pausing/backgrounding if allowed: content version, run ID, wave/phase, tower and hero mutable state, element ranks, gold, base HP, spawned/pending enemy state, projectiles, status timers and simulation timestamp. Write temp → verify → replace; retain prior valid snapshot. Never commit save files. Persist permanent progression on server and cache for offline read. Sync queued end-of-run claims on reconnect with idempotent run IDs; mark rewards pending until verified, never promise anti-cheat security from offline clients.

## Backend domain operations
Authenticate; return profile/catalog/owned heroes; register run; validate/award completion (idempotent); spend fragments and unlock hero atomically; verify purchase/token and grant once; reconcile refunds and restore entitlements. Treat repeated network callbacks safely. No hardcoded secrets or production endpoints in client/repo. Scope the account recovery and offline entitlement policy before production.

## Android targets and quality gates
Verify current Google Play policy/target API near release; do not hardcode old SDK guidance. Real device tests across performance tiers, landscape layouts/safe areas, pause/resume, airplane mode, 30/60 FPS, memory/battery, rapid tapping and purchase lifecycle. No CI badge or runnable command may be claimed until actual project exists.
