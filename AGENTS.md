# AGENTS.md

## Cursor Cloud specific instructions

### What this is
- **마이루디 (Mai Rudi)** — a client-side drum/rhythm practice web app. The entire app is a single static file: `index.html` (HTML + inline CSS + vanilla JS). There is **no backend, no build step, no package manager, and no dependencies**.
- Persistence is browser `localStorage`. Deployed as a static site on Vercel (`vercel.json` → `cleanUrls: true`).

### Running it (development)
- Serve the repo root as static files and open the app. Microphone/Web Audio features require a secure context, so serve over `http://localhost` (not `file://`):
  - `python3 -m http.server 8000` → open `http://localhost:8000/`
- There is **no lint, no test, and no build** tooling configured in this repo. Testing is manual, in-browser.

### Gotchas
- The 🥁 트레이닝 (Training) tab uses `getUserMedia` (microphone) for hit detection — needs mic permission and a secure context. The 🎛️ 메트로놈 (Metronome) and 📊 통계 (Stats) tabs work without mic.
- The optional "AI Coach" feature calls `https://api.anthropic.com/v1/messages` directly from the browser with **no API key/header**, so it will fail outside a credential-injecting sandbox. It is non-essential; core features work offline.
