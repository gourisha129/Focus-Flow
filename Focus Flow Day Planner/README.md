# FocusFlow ✦

A student-friendly productivity dashboard built with **React + Vite** and a small **Node.js/Express** backend. FocusFlow combines tasks, a custom focus timer, study-video search, an AI study assistant, themes, and a gamified Focus Universe.

## Features

- Dashboard for tasks and focus progress.
- Custom focus timer with start/pause/reset controls and a completion chime.
- Focus Universe rewards: completed sessions earn stars; focus time earns Focus Points; planets unlock as points accumulate (10-point threshold in this version).
- Groq-powered AI assistant (API key stays on the backend).
- YouTube Data API video search.
- Multiple color themes and profile/preferences.
- Local browser storage for demo preferences and progress; data is not automatically synced between devices.
- The login screen is a **demo/local sign-in**, not secure production authentication.

## Requirements

- Node.js 18+ (Node.js 20+ recommended)
- npm
- Internet connection for AI and YouTube API features

## Run locally

1. Download/clone this repository and open the `FocusFlow` folder in VS Code.
2. Open a terminal in the project root (the folder containing `package.json` and `server.js`).
3. Install dependencies:

   ```bash
   npm install
   ```

4. Copy `.env.example` to a new file named `.env` in the project root. On Windows PowerShell, run:

   ```powershell
   Copy-Item .env.example .env
   ```

5. Open `.env` and replace the placeholders with your own keys:

   ```dotenv
   GROQ_API_KEY=your_groq_key_here
   GROQ_MODEL=openai/gpt-oss-120b
   YOUTUBE_API_KEY=your_youtube_api_key_here
   API_PORT=3001
   ```

6. Start the frontend and backend together:

   ```bash
   npm run dev
   ```

7. Open the local Vite URL shown in the terminal, usually `http://localhost:5173`. Keep the terminal running.

## Get API keys

- **Groq:** https://console.groq.com/keys
- **YouTube Data API v3:** https://console.cloud.google.com/ — choose/create a Google Cloud project, enable YouTube Data API v3, and create an API key under APIs & Services → Credentials.

## Security: read before pushing to GitHub

- **Never commit `.env` or share its contents.** `.gitignore` excludes `.env` and other local env files while allowing the safe template `.env.example`.
- Do not put API keys in `src/`, React code, screenshots, README, or any variable beginning with `VITE_`. Vite variables are exposed to the browser. The backend should read secrets from `process.env`.
- Before pushing, check the Git changes and confirm `.env` is not listed. If a real key was ever committed, deleting the file is not enough: revoke/rotate that key in its provider console.
- Restrict the YouTube key to YouTube Data API v3 in Google Cloud where possible. Keep Groq keys private.

## Push to GitHub (beginner steps)

1. Create a **new empty repository** on https://github.com/new. Do not add a README there if you are using this project README.
2. Open a terminal in the `FocusFlow` folder and run:

   ```bash
   git init
   git add .
   git status
   ```

3. Check the `git status` output carefully. It should **not** list `.env` or `node_modules`. If `.env` appears, stop and fix `.gitignore` before continuing.
4. Commit the project:

   ```bash
   git commit -m "Prepare FocusFlow project for GitHub"
   ```

5. Replace `YOUR-USERNAME` and `YOUR-REPOSITORY` with your GitHub details, then run the commands GitHub shows for connecting an existing repository. Usually:

   ```bash
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
   git push -u origin main
   ```

## Troubleshooting

- If you change `.env`, restart the dev server with `Ctrl+C` and `npm run dev`.
- If AI reports a missing key, confirm `.env` is in the project root beside `server.js`, and the variable is named `GROQ_API_KEY`.
- If YouTube search fails, confirm the key is correct and YouTube Data API v3 is enabled for its Google Cloud project.
- If a secret is accidentally pushed, revoke it immediately in the provider console and create a replacement.

## Project structure

```text
FocusFlow/
├── .env.example
├── .gitignore
├── package.json
├── server.js
├── vite.config.js
└── src/
    ├── App.jsx
    ├── main.jsx
    └── styles.css
```
