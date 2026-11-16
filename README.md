# AINNO-IO

Source of https://ainno.io (Jekyll on GitHub Pages). Every push to `main` goes live.
The site is edited through Git only (no CMS).

## Pages

| URL | File |
|---|---|
| `/`, `/en/` | `index.html`, `en/index.html` |
| `/nuasmeninimas/`, `/en/anonymisation/` | `nuasmeninimas/index.html`, `en/anonymisation/index.html` |
| `/privacy/`, `/en/privacy/` | `privacy/index.html`, `en/privacy/index.html` (text in `_data/privacy_policy*.yml`) |
| `/contact/`, `/blog/` | redirects to the homepage |

All pages use `_layouts/landing.html` (fonts self-hosted in `fonts/landing/`, Content-Security-Policy in the layout).
Contact forms post to Web3Forms (`_data/contact.yml`); phone country codes are in `_data/phone_codes.yml`.

## Run locally

    bundle exec jekyll serve --host 127.0.0.1 --port 4000 --livereload
