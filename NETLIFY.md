# Deploy BuildGPT on Netlify

BuildGPT is a full-stack app (accounts, database, AI). This zip is the **source**. Netlify builds it for you. Do not drag the zip onto Netlify as a static site.

## What you need first

1. A free [Neon](https://neon.tech) Postgres database. Copy the connection string (`postgresql://…?sslmode=require`).
2. A Gemini API key from [Google AI Studio](https://aistudio.google.com/apikey) (chat, MVP, portfolio, resume).
3. A long random secret (32+ characters) for sessions.

## Deploy

1. Unzip `BuildGPT-netlify.zip`. Open the **BuildGPT** folder. You should see `package.json`, `netlify.toml`, and `src` next to each other.
2. Put that folder in a GitHub repo (new repo → upload those files as the repo root).
3. In [Netlify](https://app.netlify.com): **Add new site → Import an existing project → GitHub**.
4. Pick the repo. Build settings are already in `netlify.toml`:
   - Build command: `npm run build`
   - Publish directory: **`dist`** (never `dist/client`)
   If the Netlify UI still says `dist/client`, change it under **Site configuration → Build & deploy → Build settings**, then redeploy.
5. **Before the first successful sign-in**, open **Site configuration → Environment variables** and add:

| Name | Value |
|---|---|
| `DATABASE_URL` | Neon connection string (required for accounts) |
| `BETTER_AUTH_SECRET` | Your long random string |
| `BETTER_AUTH_URL` | Your live site URL, e.g. `https://your-site.netlify.app` |
| `VITE_AUTH_ENABLED` | `true` |
| `GEMINI_API_KEY` | Your Gemini key |

6. Trigger a new deploy so those variables apply.
7. Open the site → **Create a free account** with **email + password** (at least 8 characters).
8. Open Studio and use Chat, MVP, Portfolio, or Resume.

## After it is live

- Sign in on Netlify is **email + password**. Google / X stay on the Grok-hosted copy.
- If sign-in fails, the env vars above are almost always missing or `BETTER_AUTH_URL` does not match the site URL. Fix them and redeploy.
- If AI times out, generate again — you can still write and save by hand.
- Never put API keys or `DATABASE_URL` inside the repo.

Founded by Saivignesh Koturi.
