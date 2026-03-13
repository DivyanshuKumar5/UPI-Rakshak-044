# UPI Rakshak 🛡️
**Graph-Based UPI Payment Fraud Detection Platform**

---

## Fix Applied
The 404 error was caused by Vercel's routing config conflicting with the builds config.
This version uses Vercel's **auto-detection** — no custom routes needed:
- `index.html` at root → served as homepage automatically
- `api/*.js` files → served as serverless functions automatically

---

## Deploy to Vercel (5 minutes, free)

### Step 1 — Get Anthropic API Key
Go to [console.anthropic.com](https://console.anthropic.com) → API Keys → Create key

### Step 2 — Push to GitHub
```bash
git init
git add .
git commit -m "UPI Rakshak initial deploy"
git remote add origin https://github.com/YOUR_USERNAME/upi-rakshak.git
git push -u origin main
```

### Step 3 — Deploy on Vercel
1. Go to [vercel.com](https://vercel.com) → New Project → Import your GitHub repo
2. **Settings → Environment Variables → Add:**
   - Name: `ANTHROPIC_API_KEY`
   - Value: `sk-ant-...` (your key)
3. Click **Deploy**

✅ Your site will be live at `https://upi-rakshak-xxx.vercel.app`

### Alternative — Vercel CLI
```bash
npm install -g vercel
cd upi-rakshak
npm install
vercel
# When prompted, add env var:
vercel env add ANTHROPIC_API_KEY production
# Redeploy:
vercel --prod
```

---

## Project Structure
```
upi-rakshak/
├── index.html          ← Frontend (served at /)
├── api/
│   ├── analyze.js      ← POST /api/analyze
│   ├── bulk.js         ← POST /api/bulk
│   └── analyze-image.js← POST /api/analyze-image
├── package.json
├── vercel.json         ← Minimal config (just maxDuration)
└── README.md
```

---

## Why the 404 Was Happening
The old `vercel.json` had explicit `builds` and `routes` that conflicted.
Vercel v2 with `@vercel/node` + `@vercel/static` in builds array often causes routing issues.
**Solution:** Remove all builds/routes from vercel.json. Vercel auto-detects:
- Files in root → static
- Files in `/api` → serverless functions

---

## Environment Variables Required
| Variable | Description |
|---|---|
| `ANTHROPIC_API_KEY` | Your Anthropic API key from console.anthropic.com |

---

*Report real fraud: **1930** · cybercrime.gov.in*
