# Family Planner Pages

This repository contains a minimal static GitLab Pages site for Family Planner.

## Purpose

The public GitLab Pages site is intended to satisfy Google's public-facing app documentation requirements for OAuth and privacy verification while keeping the actual Family Planner application private behind a home network and Tailscale.

## Files

- `.gitlab-ci.yml` – GitLab Pages deployment pipeline
- `public/index.html` – homepage
- `public/privacy/index.html` – privacy policy
- `public/terms/index.html` – terms
- `public/styles.css` – shared styling

## Requirements covered

- Static site only
- GitLab Pages deployment from the default branch
- No Node.js or build tools
- Custom domain support
- Public-facing docs for Google verification
- No secrets, credentials, or tracking code

## GitLab setup

1. Create a new GitLab project.
2. Add this repository as the project content, or initialize the project and push the files from your local clone.
3. Ensure the default branch is the branch you want to publish.
4. In GitLab, go to Settings > Pages and configure the custom domain if you plan to use one.
5. Keep the Pages content public, but keep the actual Family Planner app private.

## Publish GitLab Pages

Create a local Git repository and push the files, for example:

```bash
git init
git checkout -b main
git add .
git commit -m "Add Family Planner Pages site"
git remote add origin git@gitlab.com:YOUR_USERNAME/family-planner-pages.git
git push -u origin main
```

GitLab will run the Pages job automatically from `.gitlab-ci.yml` and publish the contents of `public/`.

## Custom domain and DNS

Use a custom domain such as:

- `familyplanner.example.com`

Set DNS records for the domain with your DNS provider. Typical setup:

- `A` record or `ALIAS`/`ANAME` to the GitLab Pages IPs provided by GitLab
- or a `CNAME` record pointing to the GitLab Pages hostname

Check GitLab’s current Pages documentation for the exact records it expects for your domain. GitLab will provide certificate provisioning after the domain is added and verified.

## HTTPS and GitLab verification

1. In GitLab, add the custom domain under Settings > Pages.
2. GitLab will request verification and issue or provision an HTTPS certificate.
3. Wait until GitLab shows the domain as verified.
4. Make sure the Pages site is publicly accessible and the custom domain resolves correctly.

## Google requirements

Use the public Pages URL when entering the following in Google Cloud Console or Google Auth Platform:

- Homepage URL: `https://familyplanner.example.com/`
- Privacy Policy URL: `https://familyplanner.example.com/privacy/`
- Terms URL: `https://familyplanner.example.com/terms/`
- Authorized domain: `familyplanner.example.com`

Important: the actual OAuth callback URL for the private app is not the public Pages site. The real callback usually lives on the self-hosted Family Planner app behind Tailscale or another private network and may require a separate redirect URI configuration in Google Cloud.

## Google Search Console domain verification

If the domain is being used with Google services or Google Sign-In verification, verify domain ownership in Google Search Console using the DNS method or the method recommended by Google. Once ownership is verified, the domain can be associated with the relevant Google services.

## Manual actions required

Before final launch, the owner must complete the following:

- confirm the exact Google OAuth client configuration
- confirm the exact Google Calendar scopes used
- confirm the final private app URL and redirect URIs
- add the correct domain to GitLab Pages
- verify ownership in Google Search Console or Google Cloud
- confirm the app’s real privacy and deletion workflow

## Testing the published site

After deployment, open each URL and verify:

```text
https://familyplanner.example.com/
https://familyplanner.example.com/privacy/
https://familyplanner.example.com/terms/
```

Verify:

- each page loads correctly
- navigation links work
- styling is clean and readable
- the pages are publicly accessible
- no private network or Raspberry Pi details are exposed

## Security notes

- no credentials, tokens, or secrets are stored in this repository
- no tracking or analytics scripts are included
- no JavaScript is required for the site to function
- the public Pages site is intentionally simple and static
- private application internals remain hidden behind the home network and Tailscale

## Final note

This project is intentionally minimal and meant to satisfy the public documentation requirements for a private Family Planner app. The owner should review and adapt the privacy and terms content before going live with the final app.
