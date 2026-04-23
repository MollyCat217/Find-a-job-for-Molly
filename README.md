# JobRadar — Program Manager Job Finder

A single-file AI-powered job finder built for Program Manager roles in the Raleigh, NC area (Remote & Hybrid). Hosted via GitHub Pages — no backend or build step required.

## Features

- **AI-powered search** — scans LinkedIn, Indeed, Dice, Glassdoor, ZipRecruiter
- **Salary display** — prominently shows salary ranges on every card
- **Direct Apply links** — opens the real job listing in a new tab
- **Resume match scoring** — upload your resume (PDF/TXT) and get an AI % match score per listing
- **Job board** — save, apply, and filter listings (All / Saved / Applied / Strong Match)
- **Manual add** — paste any job URL or describe a role to add it

---

## How to Host on GitHub Pages

### Step 1 — Create a GitHub repository

1. Go to [github.com](https://github.com) and sign in
2. Click the **+** icon → **New repository**
3. Name it something like `jobradar` or `job-finder`
4. Set it to **Public**
5. Click **Create repository**

### Step 2 — Upload your files

**Option A — GitHub web interface (easiest):**
1. On your new repo page, click **Add file → Upload files**
2. Drag and drop both files:
   - `index.html`
   - `README.md`
3. Click **Commit changes**

**Option B — Git command line:**
```bash
git clone https://github.com/YOUR_USERNAME/jobradar.git
cd jobradar
# Copy index.html and README.md into this folder
git add .
git commit -m "Initial commit: JobRadar app"
git push origin main
```

### Step 3 — Enable GitHub Pages

1. In your repo, go to **Settings** → **Pages** (left sidebar)
2. Under **Source**, select **Deploy from a branch**
3. Set branch to `main` and folder to `/ (root)`
4. Click **Save**

### Step 4 — Access your live site

After ~60 seconds, your app will be live at:
```
https://YOUR_USERNAME.github.io/jobradar/
```

GitHub will show you the exact URL in the Pages settings.

---

## Files

| File | Description |
|------|-------------|
| `index.html` | The entire app — HTML, CSS, and JavaScript in one file |
| `README.md` | This file |

---

## Notes

- The app calls the **Anthropic Claude API** directly from the browser. It uses the API key embedded via Claude's artifact proxy — this works when opened through Claude.ai. If you host it publicly and want it to work for others, you'll need to add your own Anthropic API key.
- To add your own API key, open `index.html` and find all `fetch('https://api.anthropic.com/v1/messages', {` calls, then add to each `headers` object:
  ```js
  'x-api-key': 'YOUR_API_KEY_HERE',
  'anthropic-version': '2023-06-01',
  'anthropic-dangerous-direct-browser-access': 'true',
  ```
- Keep your API key private — do not commit it to a public repo. Consider using a backend proxy or environment variable for production use.

---

## Tech Stack

- Vanilla HTML/CSS/JavaScript — zero dependencies, no build step
- Google Fonts (Syne + DM Mono) loaded from CDN
- Anthropic Claude API (`claude-sonnet-4-20250514`) with web search tool
