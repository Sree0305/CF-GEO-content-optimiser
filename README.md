# GEO content optimiser

Transform content into GEO-optimised copy that surfaces in AI-generated recommendations.

## Setup

### 1. Clone and push to GitHub

```bash
git init
git add .
git commit -m "Initial commit"
gh repo create geo-optimiser --public --push
```

### 2. Deploy to Netlify

1. Go to [netlify.com](https://netlify.com) and click **Add new site > Import an existing project**
2. Connect your GitHub repo
3. Build settings are auto-detected from `netlify.toml` — no changes needed
4. Click **Deploy site**

### 3. Add your API key

1. In Netlify, go to **Site configuration > Environment variables**
2. Click **Add a variable**
3. Set:
   - Key: `ANTHROPIC_API_KEY`
   - Value: your Anthropic API key (from [console.anthropic.com](https://console.anthropic.com))
4. Click **Save**, then **Trigger deploy** to redeploy with the key active

## Project structure

```
geo-optimiser/
├── public/
│   └── index.html        # Frontend UI
├── netlify/
│   └── functions/
│       └── optimise.js   # Serverless proxy for Anthropic API
├── netlify.toml          # Netlify build + routing config
└── .gitignore
```

## How it works

- The frontend sends content to `/api/optimise` (a Netlify serverless function)
- The function reads `ANTHROPIC_API_KEY` from the server environment and calls the Anthropic API
- The API key is never exposed to the browser or included in the codebase
