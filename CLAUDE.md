# Project conventions for www.xiasma.com

This file is read by Claude Code at the start of each session. It captures durable conventions for editing this site.

## Brand: "Evagene" is always first letter uppercase, and the letters that follow in lowercase

The product is branded **`Evagene`**, at all times.

- Never write `EvaGene`, `evagene`, `EVAGENE` or any other casing.
- This form holds even at the start of sentences and inside headings (similar to `iPhone`, `eBay`, `dunnhumby`, `npm`).
- This applies to: body copy, page titles (`<title>`), headings (`<h1>` etc.), alt text, link text, image filenames, meta descriptions, Open Graph descriptions, JSON-LD `name` and `description` fields, `llms.txt` and `llms-full.txt`, README, and any commit messages or PR titles.

The only exception is when quoting an external source verbatim (rare on this site).

When in doubt, run a quick check before committing:

```sh
# Should return no results other than user-quoted content
grep -RIn -E "[Ee][Vv][Aa][Gg][Ee][Nn][Ee]" . | grep -v "Evagene"
```

## Other notes

- **Xiasma** (the company) keeps its conventional capitalisation: `Xiasma`, never `xiasma` or `XIASMA` in prose. (The wordmark logo renders in lowercase, but written references use `Xiasma`.)
- The site is plain static HTML for GitHub Pages &mdash; no build step, no Jekyll. Header and footer are intentionally duplicated across pages; when you change navigation or legal links, update every page.
- Images: keep the supplied logo PNGs in `assets/img/` with the descriptive filenames already in place; do not introduce new hand-drawn SVG approximations of the brand mark.
- **Preferred wordmark**: use the on-light variant (`xiasma-logo-wordmark-on-light.png` / `xiasma-wordmark-on-light-*.png`) for the page header, social cards and any new on-light surface. The charcoal variant exists but is not the preferred treatment &mdash; do not switch back to it without being asked. The on-dark variant is for the dark footer.
