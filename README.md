# HireBot — Full-stack starter

A runnable multi-company recruitment workspace starter with a React/Vite client and Express/SQLite API. The UI uses a friendly, approachable visual direction and an emoji placeholder mascot; replace it with your approved white-shirt robot artwork in `client/src` when you have the asset file.

## Included
- Company registration and sign-in (bcrypt password hashing, JWT sessions)
- Company-scoped records for jobs, candidates, applications, interviews and settings
- Job creation and open/close management
- CV upload (PDF, DOCX, TXT; 8 MB limit) and text extraction
- Optional OpenAI screening summaries using job-related criteria only
- Human-reviewed application stages; no automatic hiring/rejection
- Interview scheduling records
- AI agent instructions and automation toggles
- Dashboard metrics and responsive React interface

## Run locally
Requirements: Node.js 20+ and npm.

1. Open a terminal in `server/` and run `npm install`.
2. Copy `.env.example` to `.env`. Set `JWT_SECRET` to a long random value (at least 24 characters).
3. Optionally add `OPENAI_API_KEY` to enable AI-generated screening summaries. Without it, CVs are still stored and parsed but AI screening is marked as not configured.
4. Run `npm run dev` in `server/` (API on port 4000).
5. In another terminal, open `client/`, run `npm install`, then `npm run dev` (client on port 5173).
6. Visit `http://localhost:5173` and create a workspace.

## Production checklist — do before real customer data
- Use managed PostgreSQL, encrypted object storage and automated backups instead of local SQLite/disk uploads.
- Add email verification, password reset, MFA, rate limiting, audit logs and session revocation.
- Put CV files in private object storage; scan uploads for malware; define retention/deletion policies and candidate consent.
- Add role-based access control, invitation flows and stronger tenant isolation tests.
- Integrate a transactional email provider and calendar OAuth; the current app stores interview records but does not send invitations.
- Add background jobs/webhooks for email, calendar sync and automated follow-ups.
- Review local employment, privacy and AI regulations before processing applicant data. Keep human oversight and accommodations in the workflow.
- Add tests, observability, HTTPS, secrets management and deployment configuration.

## API overview
`POST /api/auth/register`, `POST /api/auth/login`, `GET /api/me`, `GET /api/dashboard`, CRUD-oriented endpoints under `/api/jobs`, `/api/candidates`, `/api/applications`, `/api/interviews`, and `/api/settings`. Authenticated endpoints require `Authorization: Bearer <token>`.

This is an implementation starter, not a deployed hosted service. External email/calendar integrations and background automation are not connected yet.
