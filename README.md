# City Center Neighborhood Association (CCNA) — Static Site

This repository contains a simple static homepage for the City Center Neighborhood Association.

Goal: deploy the contents of this folder to Cloudflare Pages and serve it from `ccna53214.org`.

Prerequisites
- A GitHub account (to host the repo)
- A Cloudflare account managing `ccna53214.org`
- Git installed and available in PowerShell

Quick publish (recommended flow: GitHub → Cloudflare Pages)

1. Create a GitHub repo (or use the GitHub web UI). Then run these commands in PowerShell from this folder:

```powershell
cd 'C:\Users\andyv\OneDrive\Documents\Development_Projects\CCNA'
git init
git add .
git commit -m "Initial CCNA site"
git branch -M main
# replace <your-username> and repo name below
git remote add origin https://github.com/<your-username>/ccna-site.git
git push -u origin main
```

Optional: use GitHub CLI to create the repo and push in one step:

```powershell
gh repo create ccna-site --public --source=. --remote=origin --push
```

2. Create a Cloudflare Pages project:
- Cloudflare Dashboard → Pages → Create a project → Connect your GitHub repo `ccna-site`.
- Production branch: `main`
- Framework: None
- Build command: (leave blank)
- Build output directory: `/` (root)

3. DNS: Remove Linktree records and add the custom domain in Pages
- In Cloudflare Dashboard → DNS, delete any CNAME or A records currently pointing your domain to Linktree (e.g., CNAME `@` or `www` -> `linktr.ee`).
- In your Pages project → Custom domains → Add `ccna53214.org` (and optionally `www.ccna53214.org`). Cloudflare will auto-provision TLS and create/verify required DNS records for you since the domain uses Cloudflare.

4. Test
- Visit `https://ccna53214.org` after deployment and DNS/SSL provisioning completes (allow a few minutes).

Troubleshooting
- If the site still resolves to Linktree after removing CNAMEs, clear Cloudflare cache and perform a full refresh in your browser (Ctrl+F5).
- If Pages asks for a DNS record for verification, copy the exact record from the Pages UI and add it in Cloudflare DNS.

Next steps I can do for you
- Create a `README.md` (done) and a `CNAME` file (done).
- Create the GitHub repo and push the branch for you (if you provide GitHub permissions or run the commands). 
- Walk through the Cloudflare Pages custom domain verification step and paste any verification text you see.

---

Files in this folder:
- `index.html` — homepage
- `citycentermap.png` — neighborhood map screenshot
- `README.md` — this file
- `CNAME` — file with domain for Pages
