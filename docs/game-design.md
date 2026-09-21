# Elemental Guardians — game design baseline

Status: **Approved product direction, pre-production**. This is an ORIGINAL Android game inspired by the broad genre mechanics of elemental tower defense; do not copy any third-party implementation, assets, names, map layout, UI, sounds or source code. Arrange an IP review before commercial release.

## Product pillars
1. Strategic tower placement on an original winding fixed enemy path, with gold economy, upgrades and elemental synergies.
2. **One** actively controlled hero for the whole run. Hero can move on walkable non-path space, auto-attack targets in range, be directed to a target and trigger one active ability; cannot block enemies. No mid-run hero switching.
3. **Exactly 20 fixed, deterministic waves per map/difficulty**; players learn the sequence and optimize hero, build order, element unlocks and positioning. Target 10–15 minutes on normal speed; the timing is a hypothesis for playtests.
4. Persistent replay progression: each run resets gold, towers and elements but grants account XP and hero fragments. One-time hero unlocks and per-hero mastery persist.
5. Free starter Kael; later heroes Lyra and Varek are intentionally more powerful in their specialties. Every hero is earnable with play or purchasable directly as a permanent, non-consumable IAP. Kael must be able to clear the regular 20-wave mission with skilled play.

## Playfield and run
- Android landscape; single-player isometric 2D presentation; one visible map for MVP, original winding route and roughly 35–45 potential tower positions (tune on real screens).
- Enemies follow authored waypoints; if they reach the base they damage its health. Base at zero health = defeat; clearing wave 20 = victory. No tower may obstruct path.
- Tap open build slot to preview/confirm a tower; tap existing tower to upgrade/sell; tap walkable area to move the hero; tap enemy to prioritize hero attack; dedicated hero ability button. Pause while building is a proposed accessibility setting to validate.
- Each kill grants in-run gold; building, upgrading and selling spend/return gold according to balance data. No IAP currency is usable during a run.
- Choose one starting discipline, gain one element point after waves 4, 8, 12, 16. Each point unlocks a new discipline or increases one owned discipline up to rank 2. The element tree resets after the run.
- Enemy groups/count/route/spawn intervals are authored and fixed; elite encounters at waves 5/10/15 and final boss at 20. No random upgrade offers or randomized enemy compositions in the MVP.
- Target pace assumption: 20 combat segments averaging 25s, ~3m build/element choices and ~1m menus = ~12m20s; validate with telemetry.

## Four original disciplines
| ID | German | Role |
| --- | --- | --- |
| ember | Glut | Damage over time, explosions |
| tide | Flut | Slow, control, conductive marks |
| ore | Erz | Armor penetration, heavy single-target |
| pulse | Impuls | Attack speed, chaining, resonance |

## MVP tower roster (11)
Neutral: Standardgeschütz (basic gun). Singles: Schmelzkanone (Ember), Strömungsprojektor (Tide), Railgun (Ore), Spulenwerfer (Pulse). Pairs: Dampfdruckturm (Ember+Tide), Schlackenwerfer (Ember+Ore), Plasmabeschleuniger (Ember+Pulse), Sedimentwerfer (Tide+Ore), Leitfähigkeitsgenerator (Tide+Pulse), Magnetbeschleuniger (Ore+Pulse). All towers have two upgrade tiers. Four bounded cross-tower resonance reactions are planned; specify exact formulas and loop-prevention in balancing stories.

## Heroes
| ID | Role | Passive / active | Unlock |
| --- | --- | --- | --- |
| kael | Free versatile starter | -5% neutral tower construction cost; temporarily overcharge a selected tower | Free from first start |
| lyra | Stronger group/pulse specialist | Pulse towers +12% damage; area chain-lightning ability; Tide+Pulse synergy | 800 fragments OR one-time store purchase (price hypothesis €4.99) |
| varek | Stronger armored-target specialist | Ore towers penetrate +15% armor; damaging armor-reducing shockwave; Ember+Ore synergy | 2400 fragments OR one-time store purchase (price hypothesis €9.99) |

Hero numbers above are **initial balance assumptions**, not validated. Hero auto-attacks, movable position and an active cooldown ability are mandatory. If KO, hero respawns after a configured interval. Exactly one hero per run; owned heroes have five persistent mastery ranks earned by using them. Bought and earned copies have the same gameplay features. Advanced heroes offer real power advantages; do not misleadingly describe monetization as purely cosmetic or competitively equal. No hero-only purchase-exclusive mechanics; no consumable power purchases at MVP.

## Persistent economy
- Profile XP unlocks future difficulty tiers; universal **hero fragments** unlock heroes. Fragment income per completed/failed run (total, not cumulative across rows): wave 1–4 = 10, 5–9 = 25, 10–14 = 50, 15–19 = 75, wave 20 cleared = 100. Award once per run ID; tune these values via tests. One-time mission milestones may add rewards separately.
- Lyra 800 fragments, Varek 2400; no Lyra prerequisite to unlock Varek. A player can save directly for any hero. Direct purchase is an alternative to fragments, not an additive fee. Purchased or earned hero remains unlocked absent a valid purchase reversal without an independent earned entitlement.
- Three difficulty tiers intended, but only first normal tier needs complete balancing for first playable vertical slice. New map, endless mode, leaderboards, seasons, battle pass, PvP and daily challenges are OUT of MVP.
- Avoid energy timers, mandatory ads, loot boxes, paid revives and intentionally frustrating time gates.

## Acceptance criteria for full MVP
A new player can clear 20 deterministic waves with Kael through strategic skill; every completed/failed run grants precisely one valid reward; Lyra/Varek may be earned or purchased; hero choice is locked per run; saves resume correctly; platform payments are verified before entitlements; game remains understandable and performant on representative Android devices. Test balancing and purchase propensity rather than treating assumptions as facts.
