# taylortabile-site

Taylor Tabile's personal website — plain static HTML, hosted on **Vercel**, auto-deployed from **GitHub**.

## How publishing works

Every time you `git push` to this repo, Vercel rebuilds and the live site updates in ~10–30 seconds. There is no separate "publish" step.

```
edit / add a file  →  git push  →  live
```

## Structure

```
index.html                    → the homepage (served at /)
marketing-roi-calculator.html → /marketing-roi-calculator
about.html etc.               → any top-level page (about.html → /about)
blog/
  index.html                  → the blog listing page (/blog)
  <slug>.html                 → one file per post (/blog/<slug>)
  _template.html              → post skeleton (NOT published — see .vercelignore)
vercel.json                   → cleanUrls on (pages serve without .html)
.vercelignore                 → files kept in repo but not deployed (_*.html)
```

Clean URLs are on, so link to pages **without** `.html` (`/blog`, `/marketing-roi-calculator`),
and always use **relative** internal links (`/`, `/#contact`) — never hard-code the domain.

## Add a page

1. Drop `something.html` in the root (or a subfolder).
2. `git add -A && git commit -m "Add page" && git push`
3. Live at `/something`.

## Publishing a blog post (the workflow)

Posts are full standalone HTML files built from `blog/_template.html`. The fast path
is to let **Claude** do it:

> Ask Claude: *"write a blog post about \<topic\>"* (or paste a draft). Claude fills
> `blog/_template.html`, saves it as `blog/<slug>.html`, adds a card to `blog/index.html`,
> commits, and pushes. Live at `/blog/<slug>` in ~20s. You just review.

Doing it by hand:
1. Copy `blog/_template.html` → `blog/<slug>.html`; fill every `{{PLACEHOLDER}}` (the
   file's top comment is the checklist). Delete the optional VIDEO/FAQ blocks if unused.
2. Add a matching `<a class="post-card">` inside `blog/index.html` (newest first).
3. `git add -A && git commit -m "New post: <slug>" && git push`

**Rules for every post:** complete HTML document; internal links relative & on-site;
keep `<title>` / meta description / canonical / JSON-LD headline in sync; slug = file name = canonical path.

## Preview locally

Open the file directly in a browser, or from this folder run any static server, e.g.:
```
python3 -m http.server 8080   # then visit http://localhost:8080
```

## Notes

- Homepage lives at `index.html` — keep the root file named `index.html`.
- Brand: Oswald + IBM Plex Sans, black (`#111`) / white. New pages should reuse the nav/footer from an existing page so the site stays cohesive.
- Canonical domain is **taylortabile.net** (repo is public so every push deploys).
