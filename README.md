# hiring.sassi.digital

Public-facing portfolio for `hiring.sassi.digital`. Permanently in redacted mode — recruiters request the full CV via the in-page form, which routes to my inbox via Formspree.

## What's in this repo

```
.
├── index.html         # The site (single file, all CSS/JS inline)
├── avatar.webp        # Anonymous iridescent profile image
├── _headers           # Cloudflare Pages security headers
├── _redirects         # Cloudflare Pages redirects (currently empty)
├── robots.txt         # Indexable
├── sitemap.xml        # Single-page sitemap
└── README.md          # This file
```

Everything is static. No build step. No dependencies. Push to `main` → Cloudflare Pages deploys.

## Local preview

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

Or just open `index.html` directly in a browser.

## Deploy (Cloudflare Pages)

This repo is wired to Cloudflare Pages with these settings:

- **Build command:** _(none)_
- **Build output directory:** `/`
- **Production branch:** `main`

Custom domain: `hiring.sassi.digital` (subdomain of `sassi.digital`).

## Editing content

The whole site is in `index.html`. Key sections:

| What                          | Where                                              |
| ----------------------------- | -------------------------------------------------- |
| Hero name / role / location   | `<header class="hero">` block, around line 905     |
| About prose                   | `<section id="about">`                             |
| Skills                        | `<section id="skills">`                            |
| Experience timeline           | The `roles` JS array near the bottom (~line 1010)  |
| Education / Languages / Certs | `<section id="education">`                         |
| Formspree endpoint            | `const FORMSPREE_ENDPOINT = '...'` near the bottom |

## Formspree

The Request-CV form posts to `https://formspree.io/f/meevbedn`. To rotate or change the endpoint, edit the constant in `index.html`.

In the Formspree dashboard:

- **Allowed domains:** `hiring.sassi.digital` (lock to prevent off-site POSTs)
- **Spam protection:** enable reCAPTCHA or built-in filter
- **Notifications:** to your private inbox
