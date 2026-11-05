# Backup and recovery

## Database (Neon)
- Neon keeps point-in-time history of every branch (free tier: limited window). Before any risky migration: create a branch from `production` named `backup-YYYYMMDD` (instant copy).
- Restore: reset `production` to a timestamp or to the backup branch in the Neon console, or point `DATABASE_URL` at the backup branch.
- Practise a restore into `staging` before relying on it.

## Website and POS (Netlify)
- Every deploy is kept. Rollback: Netlify → kiro-pos → Deploys → pick a previous deploy → "Publish deploy", or revert the pull request / set `pos-version.txt` back.

## Code (GitHub)
- Every repository has full history and release tags. The original `kirotick/KIRO_POS` stays archived read-only as an extra copy.
- Keep a local clone of every repository; consider a scheduled mirror to a second provider.
