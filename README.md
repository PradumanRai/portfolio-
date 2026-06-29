# Praduman Rai — DevOps Engineer Portfolio

A single-page personal portfolio site, built with plain HTML/CSS/JS and
deployed automatically to **GitHub Pages** via a **GitHub Actions** CI/CD
pipeline — every push to `main` triggers an automated build-and-deploy run,
with no manual upload step required.

**Live site:** `https://<your-github-username>.github.io/<repo-name>/`
*(update this line once your repo is created — see Step 1 below)*

---

## What's in this repo

```
.
├── index.html                          # the entire site (HTML + CSS + JS, single file)
├── Praduman-Rai-Resume.pdf             # linked from the "Download résumé" buttons
├── .github/workflows/deploy.yml        # CI/CD pipeline: auto-deploys to GitHub Pages
└── .gitignore
```

## How the deployment pipeline works

`.github/workflows/deploy.yml` defines a GitHub Actions workflow that:

1. Triggers automatically on every push to `main` (or manually from the Actions tab)
2. Checks out the repo
3. Packages the site as a Pages deployment artifact — no build step needed, since this is a static site
4. Deploys that artifact to GitHub Pages using GitHub's official Pages deployment action

In other words: push a change, and within a minute or two the live site updates itself — no manual `scp`, no FTP upload, no clicking around in a hosting dashboard. That's a real, working CI/CD pipeline, not just a description of one.

---

## Setup — do this once

### Step 1 — Create the repository

Two naming options:

- **Cleanest URL:** name the repo exactly `<your-username>.github.io` (e.g. `PradumanRai.github.io`). GitHub treats this as a special "user site" repo and serves it at `https://pradumanrai.github.io/` — no extra path.
- **Simpler / works for multiple projects:** name it anything else, e.g. `portfolio`. It'll be served at `https://pradumanrai.github.io/portfolio/`.

Either works fine — pick whichever you prefer.

### Step 2 — Upload these files

**Option A — GitHub web UI (no command line needed):**
1. Create the new repository on github.com (public, no README/template needed — this folder already has everything)
2. On the repo page, click **Add file → Upload files**
3. Drag in `index.html`, `Praduman-Rai-Resume.pdf`, and `.gitignore`
4. For the `.github/workflows/deploy.yml` file specifically: GitHub's upload UI doesn't always preserve nested folders cleanly, so if it doesn't show up correctly, use **Add file → Create new file**, type the path `.github/workflows/deploy.yml` directly into the filename box (GitHub will create the folders for you), and paste in the file's contents.
5. Commit directly to `main`.

**Option B — Git command line (if you have Git installed):**
```bash
cd path/to/this/folder
git init
git add .
git commit -m "Initial portfolio site with GitHub Pages CI/CD"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

### Step 3 — Turn on GitHub Pages (do this *before* or right after your first push)

1. Go to your repo → **Settings → Pages**
2. Under **Build and deployment → Source**, select **GitHub Actions**
3. Save

> ⚠️ This step matters: if Pages isn't enabled with "GitHub Actions" as the source, the `github-pages` deployment environment doesn't exist yet, and the workflow run will fail with a permissions error the first time. Enable it first, then push (or just re-run the workflow from the **Actions** tab afterward if you already pushed).

### Step 4 — Watch it deploy

Go to the **Actions** tab in your repo — you'll see the "Deploy portfolio to GitHub Pages" workflow run. Once it finishes (usually under a minute), your site is live at the URL from Step 1.

Every future change — editing `index.html`, swapping the résumé PDF, anything — just needs a normal commit and push to `main`, and the pipeline redeploys it automatically.

---

## Updating the résumé download link

The "Download résumé" buttons point to `Praduman-Rai-Resume.pdf` in the repo root. If you ever rename that file, update the two `href="Praduman-Rai-Resume.pdf"` occurrences inside `index.html` to match.

## Notes on the content

This site is built directly from real résumé data and live GitHub API data (repos, languages, contribution activity) for `github.com/PradumanRai` — no fabricated metrics, project stats, or live-demo links. Project cards are explicitly labeled as hands-on practice work where that's what they are, rather than dressed up as production systems.
