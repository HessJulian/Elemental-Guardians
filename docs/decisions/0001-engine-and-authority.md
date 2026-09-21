# ADR-0001: Unity client and server-authoritative permanent progression

- Status: Proposed for BMAD architecture review
- Date: 2026-09-21

## Context
The game is a short-session Android tower defense with a local real-time hero and permanent account-based ownership of optionally purchased stronger heroes. Combat responsiveness should not require round-trip network latency; in-app purchases and earned currency cannot trust a client callback.

## Decision proposal
Use supported Unity LTS + C# for Android local simulation, Firebase Authentication for account identity, Cloud Run for a small transactional domain API, Firestore for permanent profile/entitlement data, Unity IAP + Google Play for checkout and server-side purchase validation. Keep the initial app single-player. Separate earned entitlement and verified purchase grant per hero.

## Consequences
Low-latency local combat and simple initial operations; cannot prove unmodified run results from offline clients. Cloud services incur setup/operational costs; app must support network errors and recovery. Confirm exact SDK/editor versions, costs, data protection and anti-tamper requirements before moving ADR to Accepted.
