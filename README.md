# Family Planner public pages

This repository contains the public documentation and legal pages for Family Planner, a private household planning application.

## Purpose

The site is published using GitHub Pages at https://blackholesec.tech and is intended to provide public information for Google OAuth verification and general project documentation. The actual application is private and remains outside this repository.

## Files

- `public/index.html` — homepage describing the project, Google sign-in, and Google Calendar usage
- `public/privacy/index.html` — privacy policy draft for owner confirmation
- `public/terms/index.html` — terms page
- `public/styles.css` — shared stylesheet

## Deployment

This repository is deployed with GitHub Pages using the default branch. The production domain is:

- https://blackholesec.tech

Use GitHub Pages settings to publish the site from the repository root or the `public/` output directory as configured for the project.

## Google OAuth verification requirements

This public site should clearly explain:

- what Family Planner does
- who it is for
- that it is a private household planning application
- why Google sign-in is used
- how Google Calendar access is used
- that the app is not an AI imagery application
- that it does not generate, modify, or distribute AI-generated intimate imagery
- a privacy policy and terms page for the public site

## Notes

- No secrets, credentials, tokens, or private configuration are stored in this repository.
- The actual app is private and is not intended to be publicly accessible.
- The privacy and terms content must be reviewed and confirmed by the owner before final publication.
- This repository does not contain the private Family Planner app or OAuth client secret material.

## Local validation

Check the static site files to confirm that:

- the homepage explains the application clearly
- stylesheet links resolve correctly
- Privacy Policy and Terms links work
- no GitLab references remain
- no placeholder verification wording remains
- no credentials or sensitive configuration are included

## Validation status

The repository content was reviewed for the required Google verification fixes. Live URL verification was not performed from this environment, so no claim is made that the production site has already passed Google review.
