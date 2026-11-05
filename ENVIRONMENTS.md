# KIRO environments

Each environment has its own database branch, credentials and deployment. Production data is never used for development or tests; test or simulated payments never reach production.

| | Local development | Automated testing | Staging | Production |
|---|---|---|---|---|
| Database (Neon project `kiro`) | branch `dev` (developer logins) | branch `qa` (tests drop and recreate tables) | branch `staging` (to create from production when the API goes live) | branch `production` |
| Credentials | `.env` files on the developer PC (git-ignored) | GitHub secret `TEST_DATABASE_URL` | Render staging environment | Render / Netlify / Neon settings |
| Website + POS | `kiro-qa-testing` local server | local server in CI | Netlify deploy previews | https://kiro-pos.netlify.app |
| Core API | `npm start` in kiro-backend/api | started by tests | Render (to create) | Render `kiro-api` (not deployed yet) |
| Payments | disabled | mocked provider | provider sandbox only | **disabled** until approved (ADR-0004) |
| Deploy approval | — | — | pull request merged | pull request merged + GitHub environment `production` (owner) |
| Logs | terminal | GitHub Actions | Render logs | Netlify / Render / Neon logs |
