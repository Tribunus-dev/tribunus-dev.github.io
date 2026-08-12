# tribunus.dev — static site

This repository powers [tribunus.dev](https://tribunus.dev), the public website for **Tribunus** — the local-first control plane for agentic engineering. Founded October 2024 by Julian Torres in San Francisco, California.

## Stack

- Pure static HTML + CSS. No build step, no JavaScript framework, no trackers, no cookies.
- Deployed to GitHub Pages from the `main` branch, root path. Custom domain `tribunus.dev` is configured via `CNAME`.
- Source for the runtime, inference engine, and agent live in their own repos under [github.com/Tribunus-dev](https://github.com/Tribunus-dev).

## Pages

| Path | Purpose |
| --- | --- |
| `/` | Company landing — hero, products, pillars, ADRs, social |
| `/company` | About Tribunus as a company — mission, pillars, product family, license, founder callout, contact |
| `/founder` | Julian Torres — bio, timeline, intellectual lineage, press |
| `/linkedin` | Canonical copy for the Tribunus LinkedIn presence (personal + company page) |
| `/blog` | Index of blog posts (rendered by a separate workflow) |
| `/enterprise` | Engineering-org / enterprise briefing |
| `/404` | Custom 404 |
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

## Editing the company story

The company narrative (mission, pillars, product family, founder callout) lives in [`/company.html`](./company.html). The four pillars are mirrored on the homepage in condensed form. Keep the two in sync.

## License

The code in this repository is released under the **GNU Affero General Public License v3** (AGPL-3.0). The site copy (text on the public pages) is released under **CC-BY-4.0** unless otherwise noted. Commercial dual-licensing is available — contact <enterprise@tribunus.dev>.

© 2024–2026 Tribunus · Founded by Julian Torres · San Francisco, California
