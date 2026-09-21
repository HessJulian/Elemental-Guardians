# Backend conventions

The intended backend responsibilities include account identity, server-owned hero fragments, once-only run rewards, transactional earned hero unlocks and validated Google Play purchase entitlements. See `../docs/architecture.md` and `../docs/data-contracts.md` for intended design and contracts. Select runtime, packages and hosting according to approved architecture decisions.

**This README does not report implementation status.** Inspect backend source/configuration on the latest `main`, related GitHub Issues/PRs and actual tests for the current state. Do not infer deployed services from planned contracts. Never commit service-account JSON, secrets, production keys or unredacted purchase tokens.
