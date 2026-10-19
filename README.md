# Notch Pals website

Static site for the Mac app **Notch Pals**, hosted on GitHub Pages. It exists so App Store Connect has a public
**Support URL** and **Privacy Policy URL**.

| URL | File |
|---|---|
| https://adhithya-karthikeyan.github.io/notch-pals/ | `index.html` (home, features, Support section with FAQ) |
| https://adhithya-karthikeyan.github.io/notch-pals/privacy.html | `privacy.html` (privacy policy) |
| any missing page | `404.html` |

Other files: `style.css` (the only stylesheet), `img/` (screenshots, app icon, favicon, Mochi sprite), `.nojekyll`.

## No data collected, on the site too

No JavaScript, no cookies, no analytics, no web fonts, no third-party requests. Every page carries a strict
Content-Security-Policy `<meta>` tag (`default-src 'none'; img-src 'self'; style-src 'self'`), so the browser itself refuses anything
else. Keep it that way: do not add trackers, embeds or CDN links.

## Preview locally

```bash
python3 -m http.server 8000 --bind 127.0.0.1 --directory .
# open http://127.0.0.1:8000/
```

`404.html` uses absolute `/notch-pals/...` paths (GitHub Pages serves it for any depth), so it only looks right when the site is
served under `/notch-pals/`. If you rename the repo or add a custom domain, update those paths and the `canonical` / `og:` URLs.

## Publishing

Published on 2026-10-19 to the **public** repo `Adhithya-Karthikeyan/notch-pals`. That repo has the contents of this folder at
its root, and GitHub Pages deploys from `main` / `/ (root)`. The app's source lives elsewhere and is not in that repo.
To update the site: edit here, copy the files into that repo, push, wait for the green deploy, then check that both URLs return 200.

## Keeping it truthful

- `privacy.html` is a converted copy of `docs/appstore/PRIVACY_POLICY.md`. Change the policy text there first, then here, and update the
  date. Apple and users read this page, so it must match the shipped app.
- Feature copy mirrors `docs/appstore/LISTING.md`. Screenshots are downscaled (1440 and 720 px wide JPEGs) copies of
  `docs/appstore/screenshots/` (`01-hero`, `02-tasks`, `08-gallery`).
- When the app is live on the Mac App Store, add a download button/link to the hero in `index.html` (there is no App Store URL yet,
  so the hero shows a plain "Mac App Store" chip).
