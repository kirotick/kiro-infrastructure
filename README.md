# kiro-infrastructure

Deployment and environment configuration: Render blueprint, environment map, Netlify and Neon settings, backup and recovery notes.

Part of KIRO (Kitchen Intelligence & Restaurant Operations). Owner: @kirotick. Migrated with full history from `kirotick/KIRO_POS` (commit `252de09`), see kiro-documentation/governance/REPOSITORY_MIGRATION_PLAN.md.

## What this repository owns
- `render/render.yaml` (core API and payments services)
- `ENVIRONMENTS.md` (local / testing / staging / production)
- Backup and recovery procedure

Nothing here may be copied into another KIRO repository; other repositories use it by version or through its API.

## Depends on
- Deploys **kiro-backend** and **kiro-payments**; **kiro-web** is deployed by Netlify from its own repo

## Build
Nothing to build. Render reads `render/render.yaml` when you create a Blueprint from this repo.

## Test
CI checks for committed secrets. Changes are reviewed like code.

## Branches, reviews and releases
`main` is production and protected: changes arrive only by pull request with passing checks (see CONTRIBUTING.md). Versions follow semantic versioning; every release is a git tag `vMAJOR.MINOR.PATCH` with notes in CHANGELOG.md, so each deployment maps to one exact commit. Rollback = redeploy the previous tag.

## Security
See SECURITY.md. Never commit secrets: `.env` files are ignored, and secret scanning with push protection plus gitleaks in CI block them.
