# BuildGPT

Independent AI studio for small MVPs, portfolios, a working chatbot, and free ATS resume writing.

Founded by Saivignesh Koturi.

**Tagline:** Build the small thing. Tell the story. Pass the screen.

The studio writes the **product** you asked for — resume, portfolio, named MVP, or a direct chat answer — not a roadmap.

## Features

- Chat — a working assistant that answers the question
- MVP studio — a named product with pitch and fields, not a two-week plan
- Portfolio — a finished site you can export
- ATS resume — a finished resume you can copy or download
- Accounts — email + password on Netlify; Google / X on the Grok-hosted copy
- Light / dark theme

## Deploy on Netlify

This repo is the source. Netlify must build it (`npm run build`). Publish directory is **`dist`**, never `dist/client`.

Full steps: [NETLIFY.md](./NETLIFY.md).

Required env vars: `DATABASE_URL`, `BETTER_AUTH_SECRET`, `BETTER_AUTH_URL`, `VITE_AUTH_ENABLED=true`, `GEMINI_API_KEY`.

## Scripts

- `npm run dev` — local development
- `npm run build` — production build
- `npm run typecheck` — TypeScript
