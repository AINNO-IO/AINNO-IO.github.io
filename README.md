# AINNO website – ainno.io

Source of **https://ainno.io**, the website of AINNO (MB AI Sprendimai, Vilnius).
Built with Jekyll and hosted on GitHub Pages.

- **Every push to `main` goes live** in about a minute. Make larger changes on a branch, check them, then merge.
- The site is edited **through Git only** (there is no CMS).

## Pages

| URL | File |
|---|---|
| `/` · `/en/` | `index.html` · `en/index.html` |
| `/nuasmeninimas/` · `/en/anonymisation/` | `nuasmeninimas/index.html` · `en/anonymisation/index.html` (document PII masking product page) |
| `/privacy/` · `/en/privacy/` | `privacy/index.html` · `en/privacy/index.html` (text in `_data/privacy_policy.yml` / `privacy_policy_en.yml`) |
| `/contact/` · `/blog/` | redirects to the homepage |

Visitors whose browser is not set to Lithuanian are sent from `/` to `/en/` (unless they picked a language with the LT / EN switch).

## Structure

```
_layouts/landing.html        layout for every page (head, SEO, security policy, form script)
_includes/landing/           header, footer, phone field, privacy page body
_includes/seo.html           title, description, Open Graph, JSON-LD
_data/contact.yml            Web3Forms settings for the contact forms
_data/phone_codes.yml        country codes for the phone field
css/landing.css              shared styles (most styling is inline in the pages)
css/landing-fonts.css        self-hosted Inter + Space Grotesk (fonts/landing/)
img/  vdo/                   images and videos
```

## Adding or changing a page

- Front matter: `layout: landing`, `lang: lt` or `en`, `title`, `description`; for pages with a translation also `lt_url` and `en_url` (used by the language switch and `hreflang`).
- Optional SEO fields: `full_title` (exact browser title), `keywords`, `header.og_image` (1200×630 share image), `og_image_alt`.
- New pages appear in `sitemap.xml` automatically.
- Contact forms post to Web3Forms; set a hidden `subject` so requests can be told apart.

## Security rules

- The layout sets a **Content-Security-Policy**: scripts, styles, fonts, images and media load only from ainno.io, and forms / requests may only go to `api.web3forms.com`.
  Adding an external service (analytics, chat, embedded video, another form endpoint) means adding it to the policy in `_layouts/landing.html` – otherwise the browser blocks it.
- Fonts are self-hosted on purpose (no visitor data sent to Google Fonts). Keep it that way.
- Do not add third-party scripts without a review; update the privacy policy if a new service receives visitor data.

## Run locally

```
bundle exec jekyll serve --host 127.0.0.1 --port 4000 --livereload
```

## Check a deploy

```
gh api repos/AINNO-IO/AINNO-IO.github.io/pages/builds/latest --jq '.status + " " + .commit'
```
