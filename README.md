# 2XR Player website

A static, responsive landing page for `2xr.me`. It contains no APKs, download
links, account flows, analytics, third-party scripts or remote font requests.

The owner has authorized a public site with a private source repository. The
private repository is `dklimoff/2xr.me`. GitHub currently refuses Pages activation
with HTTP 422: "Your current plan does not support GitHub Pages for this
repository." The site has not been deployed and DNS has not been changed.

## Preview

From this directory, run:

```sh
python3 -m http.server 4173 --bind 127.0.0.1
```

Open `http://127.0.0.1:4173/`. The site requires no package installation or build.
Its public files are `index.html`, `styles.css`, `assets/`, `.nojekyll` and `CNAME`.
Keep this README and the `publishing/` directory outside the deployed artifact.

## Design

The existing pixel wordmark and orange accent are adapted from the player's
launcher SVG. The layout pairs dark neutral surfaces, large type and a cinematic
landscape with short descriptions of video formats, personal sources and the
platforms in development. All navigation is native in-page navigation, with
keyboard focus indicators, a skip link, responsive layouts and reduced-motion
support. Device text describes development targets, not certified compatibility.

## Future GitHub Pages setup

`publishing/github-pages.yml.example` is an inactive workflow template. It
deploys only the explicit public files from this repository and never packages
application files, APKs or research material. After the account supports Pages for private repositories,
copy it to `.github/workflows/website.yml`, enable Pages with GitHub Actions and
set the custom domain in the Pages settings to `2xr.me`. A CNAME file alone does
not configure a custom domain for an Actions deployment.

A private source repository does not make a standard Pages website private.
GitHub Pages from a private repository requires an eligible GitHub plan.

The existing Webnames nameservers can stay in place. In the domain's DNS record
editor, configure the following after attaching the domain to GitHub Pages:

| Type | Host | Value |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | dklimoff.github.io. |

At Webnames, the apex host may be represented as an empty name instead of `@`.
Check the editor's labels before saving. Preserve unrelated records. Once DNS
validates and GitHub provisions the certificate, enable HTTPS enforcement.

References:

- [GitHub custom domain configuration](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [GitHub Pages custom workflows](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages)
- [Webnames DNS record editor](https://www.webnames.ru/faq/nastrojka-dns/dobavit_zapis_na_dns_servery_webnames_ru)

## Hero artwork

`assets/hero.webp` was generated with the built-in image_gen tool and encoded
as WebP for the site. It is an illustrative landscape, not an app screenshot
or a claim about a real location.

Prompt: Cinematic photorealistic 16:9 panoramic snow-capped mountains and dark
glacial lake at blue hour, narrow warm sunrise horizon, dark navy and
desaturated teal with gold highlights, central/right massif, open darker
upper-left sky, natural rock detail and soft mist. No people, devices, glasses,
logos, text, UI, stars, or watermarks.
