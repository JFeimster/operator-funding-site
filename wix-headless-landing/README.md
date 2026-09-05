# Moonshine Capital — external landing page

This folder is a static, no-build landing page intended for an external frontend while Wix continues to run the existing Distilled Funding business site and business apps.

## Fastest path: Wix Headless Drop

1. Download or zip the contents of this folder with `index.html` at the ZIP root.
2. Open https://www.wix.com/headless/drop
3. Drop the folder or ZIP.
4. Wix creates a new managed headless project and hosts it on its CDN with SSL.
5. After review, connect a custom subdomain from the existing `distilledfunding.com` domain to that headless project.

Wix serves uploaded static files as-is; there is no build step and no server runtime in this landing page.

## External-host path: Cloudflare Pages

This folder can also be deployed as a static Pages project with no build command. Use `wix-headless-landing` as the output/root directory.

For a Wix-managed domain, the least disruptive production pattern is a subdomain such as `home.distilledfunding.com` or `go.distilledfunding.com`. Add the subdomain as a custom domain in Cloudflare Pages first, then add the CNAME value Cloudflare provides in Wix DNS.

Do not move the current Wix production domain or DNS until the preview is approved.

## Current CTA

Primary application CTA points to:

https://www.distilledfunding.com/apply

## Branch

`wix-headless-landing-v1`
