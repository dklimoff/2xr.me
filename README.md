# 2XR Player website

Static website for [2xr.me](https://2xr.me/), hosted on GitHub Pages from
[dklimoff/2xr.me](https://github.com/dklimoff/2xr.me).

## Content

Downloads are the primary purpose of the page. Android/Quest APK and Apple Silicon
macOS DMG choices appear first, followed by upcoming store channels and Boosty
support. Every unavailable channel states Coming soon and has no download link.
Below them, the page shows the approved Capsule interface preview, supported
devices and three compact sections for sources, spatial formats and image/control.
INSV groups Sphere, Wide and Tiny Planet together. Passthrough availability is
qualified by compatible media rather than promising it on a particular device.

Google Play, Meta Quest Store, APK and Apple Silicon macOS DMG options are intentionally unavailable placeholders.
APKs and the macOS DMG will be uploaded as assets in the separate public
[dklimoff/2xr](https://github.com/dklimoff/2xr) release repository. Once a release
is published, show its version on the site and point the APK and DMG buttons to its
versioned release page, such as
`https://github.com/dklimoff/2xr/releases/tag/v1.0.N`. The general latest-release
URL is `https://github.com/dklimoff/2xr/releases/latest`. Store URLs remain pending.
Preparing a release link does not activate downloads; activate a channel only
after a binary release is explicitly requested and its files are available.
Boosty remains plain text until the user supplies the exact support-page URL.
No APKs, DMGs, analytics, third-party scripts or remote fonts are included in the site.

## Local preview

```sh
python3 -m http.server 4173 --bind 127.0.0.1
```

Open `http://127.0.0.1:4173/`. No package installation or build is required.

## Design

The website shares the approved Capsule palette and typography with the player:
canvas `#160f09`, panel `#211810`, full-width title section `#100b07`, text
`#fff5ed`, muted text `#c5ad99`, border `#745033` and accent `#ff9229`.
Title sections end in a straight horizontal color cut. Panels use 24 px corners;
related INSV modes form a joined capsule. The launcher pixel geometry is preserved,
with a tightly cropped SVG viewBox and Player at weight 600.

The two download choices dominate the first screen. The responsive layout uses
natural scrolling and stacks downloads before product information on phones.
The interface images are cropped screenshots of the approved HTML design reference,
not claims about installed-player or device verification. The website lists video
formats directly over the mountain background, above the illustrated controls,
with a joined device-model capsule for XREAL One, VITURE Beast and Quest 2 / 3.
Their source is
`docs/player/ui-plans/capsule-2026-10-03` in the player repository.
Android and Mac compatibility includes prominent XREAL One and VITURE Beast
labels with their original brand marks. These are display labels, not controls.
Icon sources and license notices are under `assets/icons/`.

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
