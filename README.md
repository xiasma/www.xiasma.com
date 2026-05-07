# www.xiasma.com

Static brochure site for Xiasma Limited (UK, 2002, company number 04572901). Hand-written HTML + CSS, designed to deploy to GitHub Pages with a custom domain &mdash; no build step, no Jekyll, no JavaScript framework.

## Structure

```
.
├── index.html                  Home
├── products/
│   ├── index.html              Products overview
│   └── evagene.html            Evagene featured product
├── services.html               What Xiasma builds
├── experience.html             Two decades of work + company facts + past project list
├── contact.html                Enquiry form (mailto-driven)
├── privacy.html · cookies.html · accessibility.html
├── 404.html
├── assets/
│   ├── css/main.css            Design system
│   ├── js/main.js              Mobile nav toggle (only JS on the site)
│   └── img/                    Logo PNGs (originals + sized variants), favicon set, OG card
├── llms.txt                    LLM-discovery index (llmstxt.org spec)
├── llms-full.txt               Consolidated site content for LLMs
├── sitemap.xml · robots.txt
├── CNAME                       www.xiasma.com (used by GH Pages for the custom domain)
├── .nojekyll                   Tells GH Pages to skip Jekyll processing
└── .gitignore
```

## Logo assets

Originals supplied are kept in `assets/img/` with descriptive filenames:

- `xiasma-logo-wordmark-on-light.png` &mdash; **primary** wordmark for light backgrounds (grey wordmark with red icon). Used in the page header and social cards.
- `xiasma-logo-wordmark-on-dark.png` &mdash; white wordmark with red icon, for dark backgrounds. Used in the footer.
- `xiasma-logo-wordmark-charcoal.png` &mdash; alternate, more monochrome charcoal wordmark. Kept available; not currently used on the site.
- `xiasma-mark.png` &mdash; mark only (X + burner symbol, on light).
- `xiasma-icon.png` &mdash; the burner / data icon only.

Sized display variants generated alongside:
- `xiasma-wordmark-on-light-{60,120,240}.png` &mdash; used in the on-light page header.
- `xiasma-wordmark-on-dark-{60,120,240}.png` &mdash; used in the dark footer.
- `xiasma-mark-{64,128,256}.png` &mdash; mark-only sized variants.
- `favicon.ico` and `favicon-{32,48,64,180,192,512}.png` &mdash; favicon set.
- `og-default.png` &mdash; 1200×630 social/Open Graph card.

## Local preview

The site is plain HTML and works from any static server.

```sh
python -m http.server 8000
# or
npx serve .
```

Then open `http://localhost:8000/`.

## Deploying to GitHub Pages

1. **Create the repo.** Push this directory to a GitHub repo. The repo can be named anything; for an organisation it's commonly `xiasma/xiasma.github.io` or `xiasma/www.xiasma.com`.
2. **Enable Pages.** In the repo, go to *Settings → Pages*. Under *Build and deployment*, set the source to *Deploy from a branch*, select your default branch (usually `main`) and `/ (root)` as the folder. Save.
3. **Custom domain.** GitHub will read the `CNAME` file in the repo and set the custom domain to `www.xiasma.com`. Tick **Enforce HTTPS** once the certificate has been issued.
4. **DNS records.** At your registrar, configure:
   - `CNAME` record: `www` → `<your-github-username-or-org>.github.io.`
   - Apex/root `A` records for `xiasma.com` pointing to GitHub Pages IPs (currently `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`) &mdash; or an `ALIAS`/`ANAME` to `<user>.github.io.` if your DNS supports it.
   - Add the same records for `xiasma.co.uk` if you want that domain too. The `CNAME` file in this repo is set to the primary `www.xiasma.com`; visitors to `xiasma.co.uk` should be redirected at the registrar to the primary.
5. **Verify.** Once propagated, https://www.xiasma.com/ should serve the home page and https://www.xiasma.com/llms.txt should be reachable.

## Editing content

- All copy lives directly inside the `.html` files. No CMS, no templating engine. Open a page, edit, commit.
- The header, footer and `<head>` block are duplicated across pages on purpose &mdash; keeps the site dependency-free and easy to deploy.
- When updating navigation or legal links, search-and-replace across the project to keep pages in sync.

## SEO + LLM files

- `sitemap.xml` lists every public page with last-modified dates. Update the `<lastmod>` value when you change a page.
- `robots.txt` allows everything and points to the sitemap.
- `llms.txt` is the short, navigable index for language models (per llmstxt.org).
- `llms-full.txt` is the consolidated body of the site, also for language models.
- Each page has Open Graph + Twitter card metadata, a canonical URL, and JSON-LD structured data where appropriate (`Organization`, `WebSite`, `SoftwareApplication`, `Service`, `BreadcrumbList`, `ContactPage`, `AboutPage`).

## Contact form

The Contact page form opens the visitor's email client with the form contents pre-filled (a `mailto:` flow). No backend; nothing is stored on the site. To switch to a real form-handling endpoint later (e.g. Formspree, Web3Forms), update the form's `action` attribute and remove the submit JavaScript handler in `contact.html`.

## Brand notes

- Primary red: `#E1261C`.
- Wordmark grey: `#73777B`.
- Typography: Inter (from Google Fonts) with system fallbacks; JetBrains Mono for incidental monospace.
- Logo work uses the supplied Xiasma identity (X + burner symbol with the red data icon).

## Licence

Site content © Xiasma Limited. Code is bespoke and not licensed for redistribution by default.
