# Zephyr Aquilon — landing page

Static one-page site. No build step, no dependencies, no server. Publish the
contents of this folder exactly as they are.

## Files

```
index.html      the entire page — every image is embedded inside it
og-image.png    1200×630 preview card shown when the link is shared
CNAME           custom domain for GitHub Pages
robots.txt      crawler policy
sitemap.xml     single-URL sitemap
.nojekyll       stops GitHub trying to rebuild the page — leave it be
```

## The contact form is already connected

Endpoint `https://formspree.io/f/mbgrvekr` is wired in. Your email address
appears nowhere in the site — Formspree holds it on their side and forwards
submissions to your inbox.

Each enquiry arrives titled *"Zephyr Aquilon — enquiry from [name]"* with the
sender's address as reply-to, so you can just hit reply. Free tier covers 50
submissions a month.

**Formspree only accepts submissions from a real web address** — test the form
after publishing, not by opening the file locally.

## Publish on GitHub Pages

1. Create a repository, e.g. `zephyr-aquilon-site`.
2. Commit **the contents** of this folder to the repository root — `index.html`
   must sit at the top level, not inside a `publish/` subfolder, or the site
   will 404.
3. Repo → **Settings → Pages** → Source: *Deploy from a branch*,
   Branch: `main`, Folder: `/ (root)`. Save.
4. Same page: enter `www.zephyraquilon.com` as the custom domain, tick
   **Enforce HTTPS** once the certificate is issued.
5. At your DNS registrar add these five records:

   | Type | Name | Value |
   | --- | --- | --- |
   | CNAME | www | *your-github-username*.github.io |
   | A | @ | 185.199.108.153 |
   | A | @ | 185.199.109.153 |
   | A | @ | 185.199.110.153 |
   | A | @ | 185.199.111.153 |

   The CNAME serves the site at `www`. The four A records make the bare
   `zephyraquilon.com` redirect there, so both spellings work.

DNS propagation and certificate issuance take up to 24h. Then send yourself one
test enquiry through the form.

## If you skip the custom domain

The site lives at `https://<username>.github.io/<repo>/`. In that case: delete
`CNAME`, and replace every `https://www.zephyraquilon.com/` with that address in
`index.html` (4 occurrences: canonical, og:url, og:image, twitter:image),
`robots.txt` and `sitemap.xml`. Those absolute URLs only affect link-preview
cards and search results — the page renders fine either way.

## How people reach you

Two routes: the contact form, and your LinkedIn profile (linked from the founder
bio and the footer). No email address, no phone number, no location beyond
"Lausanne, Switzerland".

## Good to know

- Fonts load from Google Fonts; offline the page falls back to system serif and
  monospace, and the layout holds.
- The three animations respect the visitor's "reduce motion" setting.
- All imagery is embedded in `index.html` — one request, nothing that can go
  missing.
- The form carries a hidden decoy field that silently discards bot submissions.
- The editable master lives in the design project. Re-export here after any
  change rather than hand-editing `index.html`.
