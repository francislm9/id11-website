# ID11 — id11.org

The ID11 website. Static HTML and CSS. No build step, no framework, no npm.
Every page is a finished file — edit it in the GitHub web editor, commit, and
Netlify publishes within about a minute.

## What is where

```
index.html          the homepage
about.html          …and 30 more pages, one file each
assets/id11.css     the entire design system — every colour, size and layout rule
assets/photos/      photography
assets/crests/      club crests
assets/alumni/      alumni carousel images
assets/accred/      AACSB, AMBA, ISC Paris marks
assets/platforms/   Apple, Spotify, YouTube icons
netlify.toml        publish directory, security headers, cache rules, 301 redirects
sitemap.xml         every page, for search engines
robots.txt          points search engines at the sitemap
```

## Checking which version is live

Every page carries a build stamp. Open the live site, view source, search for
`id11-build`. It should match the newest deploy:

```html
<meta name="id11-build" content="v4.1">
```

If the live site shows an older version than the repo, Netlify has not
redeployed — check the Deploys tab, not the code.

## Repo structure matters

`index.html` must sit at the **root of the repo**, not inside a folder. If the
repo's front page shows a single folder rather than a list of files, Netlify
will serve a 404 and the fix is to re-upload the folder's *contents*.

## Forms

Three Netlify forms, detected automatically at deploy time:

| Form name    | Where             | Goes to        |
|--------------|-------------------|----------------|
| `start`      | homepage hero     | `/thanks.html` |
| `assessment` | `assessment.html` | `/thanks.html` |
| `contact`    | `contact.html`    | `/thanks.html` |

Each carries a hidden `form-name` field and a `company` honeypot for spam.
Submissions appear under **Forms** in the Netlify dashboard. Set up email
notifications there — Netlify does not email you by default.

## Phone rules

Every phone rule lives at the bottom of `assets/id11.css`, in
`@media(max-width:699px)` blocks, then `@media(max-width:380px)`. They are last
in the cascade on purpose: anything added above them gets overridden on phones,
which is the behaviour you want.

The hero headline is deliberately different by device — Montserrat Black on
phones so it carries the screen, Bold on desktop where it runs much larger.

## Brand

Type and colour follow `ID11_BRANDGUIDE_AUG_2026`.

- Display: Montserrat — Black 900, Bold 700, SemiBold 600
- Body: Karla Regular 400
- Desktop scale 64 / 40 / 26 / 18 / 16 / 13 · Mobile 36 / 26 / 20 / 17 / 15 / 12
- Pitch Black `#0B0C0B` · Night Green `#0F2B1B` · Pitch Green `#25573A`
- Sand `#F5DFB8` · White `#FFFFFF` · Live Green `#55D93F`

## Before this goes to a real domain

- [ ] Canonical URLs, `sitemap.xml` and `robots.txt` still point at the old
      Netlify address. They must be updated to the final domain.
- [ ] Testimonials are built but switched off until real quotes exist
      (`TESTIMONIALS` list — the section does not render while it is empty).
- [ ] `privacy.html` and `terms.html` need a lawyer's read.
- [ ] Leadership pages carry 17 names and no photographs.
