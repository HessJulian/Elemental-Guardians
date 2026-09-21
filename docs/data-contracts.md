# Domain data and API contracts (proposed; not implemented)

## Stable IDs
Use stable snake_case content IDs, e.g. `hero_kael`, `hero_lyra`, `hero_varek`, `tower_standard`, `wave_01`; do not use UI display strings as keys. Each static content revision has a `contentVersion`. All write operations use authenticated account identity; never trust client-supplied player ID.

## Core entities
- `PlayerProfile`: `playerId`, `profileLevel`, `profileXp`, `heroFragments`, `highestWave`, `totalRuns`, `totalVictories`, `profileVersion`.
- `HeroDefinition`: `id`, `stats`, `passiveAbilityId`, `activeAbilityId`, `preferredElements`, `fragmentCost`, `storeProductId` (nullable for Kael).
- `HeroOwnership`: `heroId`, `earnedUnlock` (boolean), `purchaseGrants` (verified token references with current status), `masteryLevel`, `masteryXp`, `unlockedAt`; `isUnlocked` is DERIVED from earned or valid purchased grant. Refund must not revoke independently earned access.
- `Run`: `runId`, `playerId`, `heroId`, `difficultyId`, `mapId`, `contentVersion`, `startedAt`, `state`, `highestWave`, `rewardClaimedAt`; a claimed run may not claim again.
- `WaveDefinition`: ordered spawn groups, count, timing, enemy ID, wave number, deterministic map/difficulty configuration.
- `TowerInstance`: slot/position, tower ID, tier, cooldown, runtime buffs; `EnemyInstance`: waypoint progress, HP, statuses; `HeroInstance`: position, HP, ability cooldowns, buffs.
- `PurchaseLedger`: platform product ID, purchase token hash/reference, account ID, verification state, acknowledgement state, refund state, entitlement grant ID. Tokens are secrets: do not put raw token values in logs/analytics.

## API draft
| Method | Path | Contract |
| --- | --- | --- |
| GET | `/v1/profile` | Authenticated current profile |
| GET | `/v1/heroes` | Catalog and account-specific earned/purchased entitlement status |
| POST | `/v1/runs/start` | Validate selected hero access and create unique run ID |
| POST | `/v1/runs/complete` | Idempotent run-result claim; verify constraints and award once |
| POST | `/v1/heroes/unlock` | Idempotency-keyed atomic fragment spend + earned unlock |
| POST | `/v1/purchases/verify` | Verify Google Play purchase state server-side and grant once |
| GET | `/v1/config` | Versioned content and balancing config |

For purchases, treat `PENDING` as not owned until confirmed; honor cancellation/refund/revocation and restore valid purchases. For fragments, server uses the approved reward table in `docs/game-design.md`, not submitted client fragment totals. Offline run claims are provisional and cannot be accepted as proof of unmodified combat. Define a migration policy before changing content IDs or saved snapshots.
