Sri Lakshmi Goat Farm - One-page site

Short instructions:

- Files:
  - `index.html` - main page
  - `styles.css` - styles

- To open locally: open `index.html` in a browser (double-click or use a local server).
- Replace placeholder phone number `+919XXXXXXXXX` and WhatsApp link with real number.

Deploying to a domain:

- For the static HTML/site: upload the files in this folder to any static host and point your domain's DNS to the host.
- For the Angular app: build with `cd angular-app && npm run build:web`, then host the contents of `angular-app/dist/goatfarm-angular` on your static host. Configure DNS as required by your host (A or CNAME records).

Netlify deployment (recommended simple flow):

1. Sign in to Netlify and click "New site from Git". Connect your repo.
2. Configure build settings:
   - Build command: npm run build:web
   - Publish directory: angular-app/dist/goatfarm-angular
3. After deploy, go to Site settings → Domain management → Add custom domain and follow prompts.

Vercel deployment (Git-based):

1. Sign in to Vercel and import project from Git.
2. Project settings:
   - Framework Preset: Other
   - Build Command: npm run build:web
   - Output Directory: angular-app/dist/goatfarm-angular
3. Add custom domain in Vercel dashboard.

DNS record examples (replace example.com with your domain):

- Netlify (using Netlify DNS / CNAME method):
  - Create a CNAME record for www -> your-site.netlify.app
  - Optionally set an ALIAS or A record for the root domain pointing to Netlify's load balancer IPs (follow Netlify's docs).

- Vercel (recommended):
  - Add an A record for the root (@) pointing to Vercel's assigned IPs (check project settings), and a CNAME for www -> cname.vercel-dns.com

- Generic static host (using S3 + CloudFront):
  - Create an A record for your domain using the CloudFront distribution domain as an alias.

Notes on DNS TTL and propagation:
- DNS changes can take up to 24-48 hours to propagate, but often are visible in a few minutes to a few hours.
- Use online DNS checkers (e.g., https://dnschecker.org) to verify records.

Notes:
- Carousel is CSS-only using radio inputs; swap to JS if you want autoplay or swipe support.
- Content is bilingual (English + Telugu).

Git quickstart (init repo, push to GitHub, auto-build):

1. Initialize Git and create your first commit locally:

```powershell
cd C:\workforvision\goatfarm-pwa
git init
git add .
git commit -m "Initial commit - goatfarm site and angular app"
```

2. Create a new repository on GitHub (via the GitHub website), then add the remote and push:

```powershell
git remote add origin https://github.com/<your-username>/<repo-name>.git
git branch -M main
git push -u origin main
```

3. Connect to Netlify or Vercel:
 - Netlify: New site from Git -> select GitHub repo -> set build command `npm run build:web` and publish dir `angular-app/dist/goatfarm-angular`.
 - Vercel: Import project -> connect GitHub repo -> set Output Directory to `angular-app/dist/goatfarm-angular`.

4. Optional: CI is included (build workflow) — GitHub Actions workflow will build on push. Check the Actions tab on GitHub to see build runs.

If you want, I can add a GitHub Action to auto-deploy to Netlify (requires Netlify token) or to Vercel (requires Vercel token). Tell me which provider you prefer and I’ll add the deploy action.

GitHub Pages (auto-deploy from this repo)

1. This repository includes a GitHub Actions workflow that will build the Angular app and publish the contents of `angular-app/dist/goatfarm-angular` to GitHub Pages on every push to `main`.

2. After pushing, go to the repository Settings → Pages and confirm the site is published from the `gh-pages` branch (the workflow will create/update it). The published site URL will be shown there, typically: `https://<your-username>.github.io/<repo-name>/`.

3. If you want a custom domain, add it in the Pages settings and create the DNS records your domain registrar requires (usually a CNAME pointing to `<your-username>.github.io`).

Note: GitHub Pages serves static files. The Angular build output created by the workflow includes an `index.html` and required assets; the action will push them to `gh-pages` branch and update the Pages site.