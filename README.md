# Rinda Apps

Static product, privacy, and support pages for `https://apps.rinda.co`, hosted with GitHub Pages. No framework, package installation, tracking scripts, or backend is needed.

## Pages

- `/` — compact app directory, currently listing HoverLingua and OmnoryPlayer.
- `/hoverlingua/` — HoverLingua product page.
- `/omnoryplayer/` — OmnoryPlayer product overview and contact.
- `/hoverlingua/privacy/` — privacy policy for the current app.
- `/hoverlingua/support/` — setup, troubleshooting, and contact.

The website lives at the repository root: `index.html`, `assets/`, `hoverlingua/`, and `omnoryplayer/`. Each app route uses a directory with `index.html`. Local asset and navigation paths are relative and point explicitly to HTML files, so opening `index.html` directly also loads the styles, icons, and product pages.

GitHub Actions copies only the public files into the ignored `_site/` staging directory and uploads that artifact. README, LICENSE, editor files, Git metadata, and local configuration are not published.

## Local preview

From this repository:

```sh
python3 -m http.server 4318 --bind 127.0.0.1
```

Open `http://127.0.0.1:4318/`, or simply double-click the root `index.html` for a quick local preview. The HTTP server is useful for checking hosted behavior.

## Publish to GitHub Pages

1. Review the page copy and confirm `developer@rinda.co` is monitored and suitable for public support/privacy requests.
2. Commit and push to `main` when ready.
3. In `Rin-Da/apps` → Settings → Pages, choose **GitHub Actions** as the publishing source.
4. Set the Pages **Custom domain** to `apps.rinda.co`. The tracked `CNAME` documents the intended domain; for an Actions deployment it does not replace the Pages setting.
5. At the DNS provider for `rinda.co`, add a **CNAME** record for `apps` pointing to **`rin-da.github.io`**. Use this hostname without a repository path. Keep the existing apex-domain records for `rinda.co`.
6. Wait for GitHub's domain check and HTTPS certificate, then enable **Enforce HTTPS**.
7. Confirm the deployment workflow succeeds and check all listed public routes over HTTPS. If the first push preceded Pages setup, rerun **Deploy GitHub Pages** from Actions.

Configure the custom domain on GitHub before pointing DNS at it. Consider verifying ownership in the organization's Pages settings as described in GitHub's documentation.

References: [custom domains](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site), [deployment workflows](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages).

## Content accuracy before release

HoverLingua and OmnoryPlayer are marked **In testing**. Add the real App Store link and update that status once a public release is available. The example panels are explicitly labeled illustrations, not screenshots.

The privacy page reflects the current HoverLingua source: on-device capture/OCR/translation and no Mixpanel or Sentry integration. Before adding either service, update the actual app behavior, consent controls, this policy, and App Store privacy declarations together. Verify provider-generated identifiers/properties and never collect captured content in analytics or diagnostics.

The website has no client-side scripts or external fonts. GitHub's hosting privacy statement is linked in the policy. Review the policy's publisher/contact and support-message retention description before public release.

## Adding another app

Add its product, privacy, and support directories under `<app-name>/`, reuse `assets/style.css`, and add a card to the `.catalog-grid` list in `index.html`. Each card contains an icon, category, description, platform badges, release status, and a real product-page link. For an app page in `new-app/index.html`, use `../assets/style.css` for shared styles and `../index.html` to return to the directory. Nested privacy/support pages need `../../` paths. Preserve these document-relative links when adding pages. Update the visible app count. Keep detailed product content on its individual page. A project-specific privacy policy must reflect that app; HoverLingua’s policy does not cover OmnoryPlayer. Do not create another domain or repository for every app.

`.gitignore` excludes local editor files, environment/secrets files, logs, caches, and build output. It does not ignore the root website files; `_site/` is only generated staging output.

## Brand assets

The header and favicon use the original geometric R mark, copied without changes from [Rinda’s existing website](https://github.com/Rin-Da/Rin-Da.github.io/blob/master/images/favicon.png). The original Rinda logo guide was checked for the approved artwork. Use official supplied logo assets when changing the branding; do not redraw or generate replacements. App icons come from their respective production asset catalogs.
