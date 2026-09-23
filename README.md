# 2XR Player website

Static website for [2xr.me](https://2xr.me/), hosted on GitHub Pages from
[dklimoff/2xr.me](https://github.com/dklimoff/2xr.me).

## Content

The page lists Android and Apple Silicon macOS support for XR glasses, Oculus Quest devices,
video formats, media sources,
view controls, image processing, INSV playback and Oculus Quest controls.

Google Play, Oculus Store, APK and Apple Silicon macOS DMG buttons are intentionally unavailable placeholders.
APKs and the macOS DMG will be uploaded as assets in the separate public
[dklimoff/2xr](https://github.com/dklimoff/2xr) release repository. Once a release
is published, show its version on the site and point the APK and DMG buttons to its
versioned release page, such as
`https://github.com/dklimoff/2xr/releases/tag/v1.0.N`. The general latest-release
URL is `https://github.com/dklimoff/2xr/releases/latest`. Store URLs remain pending.
Preparing these links does not activate downloads; the current page stays unchanged
until a binary release is explicitly requested and its files are available.
No APKs, DMGs, analytics, third-party scripts or remote fonts are included in the site.

## Local preview

```sh
python3 -m http.server 4173 --bind 127.0.0.1
```

Open `http://127.0.0.1:4173/`. No package installation or build is required.

## Design

The palette uses three color roles: midnight slate (`#0e1418`) for the canvas,
warm ivory (`#f2eee7`) for text, and restrained burnt orange (`#c68143`) for
the 2XR mark and direct-download emphasis. Surface and border shades are
derived from the slate family. Store placeholders remain neutral; APK and DMG
placeholders carry the orange accent. Device logos precede six feature groups
with soft corners and quiet outlines.

The desktop layout uses three feature columns and compact spacing. Narrow
screens use fewer columns and preserve natural scrolling where necessary.
Icon sources and license notices are under `assets/icons/`; the Apple Silicon
mark is a minimal monochrome Simple Icons glyph used to identify the macOS build.

## Deployment

`.github/workflows/website.yml` publishes changes to the public site when
website files are pushed to `main`. It can also be run manually from Actions.
The workflow uploads only `index.html`, `styles.css`, `assets/`, `.nojekyll`
and `CNAME`. Repository documentation and application files are excluded.

The GitHub Pages source is GitHub Actions. Set `2xr.me` as the custom domain
in repository Settings / Pages; the CNAME file alone does not configure the
custom domain for an Actions deployment. Enable Enforce HTTPS once GitHub
has issued the certificate.

## Webnames DNS

Keep `ns1.nameself.com` and `ns2.nameself.com`. The following records were
verified publicly on 2026-09-15:

| Type | Subdomain | Value |
| --- | --- | --- |
| A | @ | 185.199.108.153 185.199.109.153 185.199.110.153 185.199.111.153 |
| CNAME | www | dklimoff.github.io. |

Webnames accepts all four IPv4 addresses in one A entry, separated by spaces.
Adding individual entries for the same host and type replaces the earlier value.
Use the individual record editor instead of Simple setup, which also creates a
wildcard record. Preserve unrelated DNS records.

References:

- [GitHub custom domain configuration](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [GitHub Pages custom workflows](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages)
- [Webnames multiple-address syntax](https://www.webnames.ru/help/faq)
