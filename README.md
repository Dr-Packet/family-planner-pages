# Public Pages

This repository contains a minimal static site for public-facing documentation and verification pages.

## Purpose

The public site is intended to satisfy public-facing documentation requirements for app verification, privacy information, and terms while keeping the main application private.

## Files

- `.gitlab-ci.yml` – Pages deployment pipeline
- `public/index.html` – homepage
- `public/privacy/index.html` – privacy policy
- `public/terms/index.html` – terms
- `public/styles.css` – shared styling

## Requirements covered

- Static site only
- Deployment from the default branch
- No Node.js or build tools
- Custom domain support
- Public-facing documentation for verification
- No secrets, credentials, or tracking code

## GitLab setup

1. Create a new GitLab project.
2. Add this repository as the project content, or initialize the project and push the files from your local clone.
3. Ensure the default branch is the branch you want to publish.
4. In GitLab, go to Settings > Pages and configure the custom domain if you plan to use one.
5. Keep the Pages content public while keeping the main application private.

## Publish GitLab Pages

Create a local Git repository and push the files, for example:

```bash
git init
git checkout -b main
git add .
git commit -m "Add public pages site"
git remote add origin git@gitlab.com:YOUR_USERNAME/public-pages.git
git push -u origin main
```

GitLab will run the Pages job automatically from `.gitlab-ci.yml` and publish the contents of `public/`.

## Custom domain and DNS

Use a custom domain such as:

- `app.example.com`

Set DNS records with your DNS provider. Typical setup:

- `A` record or `ALIAS`/`ANAME` to the GitLab Pages IPs provided by GitLab
- or a `CNAME` record pointing to the GitLab Pages hostname

Check GitLab’s current Pages documentation for the exact records it expects for your domain.

## HTTPS and verification

1. In GitLab, add the custom domain under Settings > Pages.
2. GitLab will request verification and issue or provision an HTTPS certificate.
3. Wait until GitLab shows the domain as verified.
4. Make sure the Pages site is publicly accessible and the custom domain resolves correctly.

## Domain verification

If the domain is being used with external verification or sign-in flows, verify domain ownership in the relevant provider using the DNS method or the method recommended by that provider.

## Manual actions required

Before final launch, the owner must complete the following:

- confirm the exact OAuth or authentication configuration
- confirm the exact scopes used
- confirm the final private app URL and redirect URIs
- add the correct domain to GitLab Pages
- verify ownership in the required provider or console
- confirm the app’s privacy and deletion workflow

## Testing the published site

After deployment, open each URL and verify:

```text
https://app.example.com/
https://app.example.com/privacy/
https://app.example.com/terms/
```

Verify:

- each page loads correctly
- navigation links work
- styling is clean and readable
- the pages are publicly accessible
- no private network or internal details are exposed

## Security notes

- no credentials, tokens, or secrets are stored in this repository
- no tracking or analytics scripts are included
- no JavaScript is required for the site to function
- the public Pages site is intentionally simple and static
- private application internals remain hidden behind the main network or private infrastructure

## Final note

This project is intentionally minimal and meant to satisfy public documentation requirements for a private app or service. The owner should review and adapt the privacy and terms content before launch.
