# grim3.org

Static site for GRiM³ (Graduate Research in Mathematics 2027, UNC Charlotte). No build step:
Cloudflare Pages serves this folder as is.

| File | Purpose |
| --- | --- |
| `index.html` | The whole site: header, sections, footer. Edit this directly. |
| `favicon.svg` | Browser tab icon (the 7-fold center of the hyperbolic tiling). |
| `og.png` | Preview image for link shares (1200×630). |
| `_headers` | Cloudflare Pages security/cache headers. |

The header design lives in `../header.template.html` + `../make_header.py`; `index.html` is a copy that has
since gained the page sections, so changes to one are not picked up by the other.

## Deploy on Cloudflare Pages

**Easiest (no Git):** Cloudflare dashboard → *Workers & Pages* → *Create* → *Pages* → *Upload assets*
→ give it a name (pages.dev names are global and many are taken, so use something specific like `grim3-conference`; the project's own `*.pages.dev` address is shown in its dashboard) → drag this `website` folder in → *Deploy*. To update later, open the project →
*Create new deployment* → upload the folder again.

**With Git (auto-deploys on every push):** put this folder in a GitHub repo, then *Create* → *Pages* →
*Connect to Git*. Framework preset: *None*. Build command: leave empty. Output directory: `/`
(or the folder name if the repo has other files).

**Command line:** `npx wrangler pages deploy . --project-name <your-project-name>` (from this folder, after `npx wrangler login`).

## Connect grim3.org

1. Project → *Custom domains* → *Set up a custom domain* → `grim3.org`.
2. If the domain is registered at Cloudflare (or its nameservers point to Cloudflare), the DNS record and HTTPS
   certificate are created automatically. If it's registered elsewhere, change the domain's nameservers to the
   two Cloudflare gives you (needed for the bare `grim3.org` address).
3. Also add `www.grim3.org` as a custom domain, then add a redirect from `www` to `grim3.org`
   (*Rules* → *Redirect Rules*) so both addresses work.
4. Check `https://grim3.org` loads with the padlock; paste it into a chat app to see the link preview.

## Before launch

- Fonts: the page uses Interstate (installed on the designer's machine only). Visitors will see the fallback
  (Barlow Condensed / Arial Narrow) until a licensed webfont is added in `index.html` via `@font-face`.
- Add the Schedule details, a contact email, and the MGSA / Principal / SAFC logos when ready.
- The Register buttons point to the Google Form from the flyer's QR code.
