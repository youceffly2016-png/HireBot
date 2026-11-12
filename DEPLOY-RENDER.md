# Deploy HireBot on Render

This repository includes a Render Blueprint (`render.yaml`) that builds the React app and serves it from the Express API on one service. SQLite and uploaded CVs are stored on a persistent Render disk.

## Deploy
1. Push the `hirebot-fullstack` folder to a new GitHub repository.
2. Sign in to Render and choose **New → Blueprint**.
3. Connect the GitHub repository and select `render.yaml`.
4. Review the service. The blueprint uses a paid Starter web service because persistent disks are not available on Render's free web services.
5. Add `OPENAI_API_KEY` in the Render environment settings if you want AI-generated screening summaries. It is optional.
6. Deploy. Wait for `/api/health` to report `{"ok":true,"service":"HireBot API"}`.
7. Open the generated Render URL and create the first company workspace.

## Important launch limitations
This is a pilot deployment configuration, not a production security certification. Before inviting real applicants, add email verification, password reset/MFA, rate limiting, audit logging, malware scanning, candidate consent and retention controls, backups, and a privacy/legal review. SQLite on a single persistent-disk instance is suitable for a controlled pilot, not high availability or horizontal scaling. Email and calendar delivery integrations are not implemented yet; interview records are stored in HireBot only.

Do not commit `.env` files or API keys to GitHub. Render generates `JWT_SECRET`; set secrets only in the Render dashboard.
