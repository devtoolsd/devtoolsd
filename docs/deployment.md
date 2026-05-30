# Deployment

## Automatic (GitHub Pages)

Every push to `main` triggers the GitHub Actions workflow at `.github/workflows/deploy.yml`:

1. Checks out the repo
2. Installs Hugo (latest extended)
3. Runs `hugo --minify`
4. Deploys `public/` to GitHub Pages

No manual steps needed. The site is live within ~2 minutes of merging a PR.

## Manual build

```bash
hugo --minify --baseURL "https://devtools.directory/"
# Output → public/
```

Upload `public/` to any static host (Netlify, Vercel, Cloudflare Pages, S3, etc).

## Custom domain

Set in `hugo.toml`:

```toml
baseURL = "https://your-domain.com/"
```

Add a `CNAME` file to `static/`:

```
your-domain.com
```

Configure DNS to point to GitHub Pages (`{username}.github.io`).

## Environment

No environment variables are needed. The site is fully static — all configuration lives in `hugo.toml` and the content files.
