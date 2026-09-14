# 2XR Player website

Static website for [2xr.me](https://2xr.me/), hosted on GitHub Pages from
[dklimoff/2xr.me](https://github.com/dklimoff/2xr.me).

## Content

The page lists supported and experimental devices, video formats, media sources,
view controls, image processing, INSV playback and Quest controls. Quest 2
is retained with testing planned. VITURE Beast remains experimental.

Google Play, Quest Store and APK buttons are intentionally unavailable placeholders.
APKs will be uploaded as assets in this repository's GitHub Releases. After the
first release is available, the APK button can point to
`https://github.com/dklimoff/2xr.me/releases/latest`. Store URLs remain pending.
No APKs, analytics, third-party scripts or remote fonts are included in the site.

## Local preview

```sh
python3 -m http.server 4173 --bind 127.0.0.1
```

Open `http://127.0.0.1:4173/`. No package installation or build is required.

## Design

The original mountain design palette is retained: charcoal and blue-black
surfaces, warm white text, neutral gray details and an orange accent. Large
store and APK buttons sit below the pixel wordmark. Device logos precede six
feature groups with thin translucent badge outlines and soft corners.

The desktop layout uses three feature columns and compact spacing. Narrow
screens use fewer columns and preserve natural scrolling where necessary.
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
