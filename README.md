# tribunus.dev — static site

This repository powers [tribunus.dev](https://tribunus.dev), the public website for **Tribunus** — an independent, founder-led software company. The company is one founder, one product, one bet. The website is exclusively about the company, the founder, and what the founder is looking for.

**Founded October 2024 by Julian Torres in San Francisco, California. Founder applying to startup accelerators in 2026.**

## The product lives elsewhere

Tessera Studio, the only product Tribunus ships in 2026, lives at **[tessera.tribunus.dev](https://tessera.tribunus.dev)**. This site (tribunus.dev) is the company-and-founder site; the Tessera site is the product site.

## Stack

- Pure static HTML + CSS. No build step, no JavaScript framework, no trackers, no cookies.
- Deployed to GitHub Pages from the `main` branch, root path. Custom domain `tribunus.dev` is configured via `CNAME`.
- Source for Tessera, the Tessera Studio app, and the other Tribunus projects live in their own repos under [github.com/Tribunus-dev](https://github.com/Tribunus-dev).

## Pages

| Path | Purpose |
| --- | --- |
| `/` | Company & founder landing — hero, the one product, the five collaboration shapes, honest status map, press |
| `/company` | About Tribunus as a company — mission, four pillars, the product in flight, license, founder callout, contact |
| `/founder` | Julian Torres — bio, TL;DR, timeline, intellectual lineage, accelerator-application callout, press |
| `/looking-for` | The five concrete asks for 2026: beta users, co-engineers, quantization researchers, advisors, investors & accelerators |
| `/tessera` | Brief on Tessera Studio with a clear link out to tessera.tribunus.dev |
| `/linkedin` | Canonical copy-paste copy for the Tribunus LinkedIn presence (personal + company page) |
| `/blog` | Index of blog posts (rendered by a separate workflow) |
| `/404` | On-brand 404 |
| `/.well-known/security.txt` | Coordinated vulnerability disclosure contact |
| `/humans.txt` | Team attribution |
| `/sitemap.xml` | Sitemap |

## Local preview

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Or with any other static server (e.g. `npx serve`).

## Editing the LinkedIn copy

The canonical copy for LinkedIn lives in [`/linkedin.html`](./linkedin.html). Each block is annotated with the LinkedIn field it targets and has a copy-to-clipboard button. When the company story changes, update the page first, then mirror to LinkedIn.

## Editing the looking-for page

The five collaboration shapes live in [`/looking-for.html`](./looking-for.html). Each shape has a "first email" with a specific subject line. Keep the names and the contact info in sync with `/index.html`.

## Editing the status map

The honest status table on the homepage (`index.html` → "honest status map") is the source of truth for "what is live, what is in dev, what is planned". Update the rows there whenever a status changes — the rest of the site will start to drift if this map drifts.

## License

The code in this repository is released under the **GNU Affero General Public License v3** (AGPL-3.0). The site copy (text on the public pages) is released under **CC-BY-4.0** unless otherwise noted. Commercial dual-licensing is available — contact <enterprise@tribunus.dev>.

© 2024–2026 Tribunus · Founded by Julian Torres · San Francisco, California
