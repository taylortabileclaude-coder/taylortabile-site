# taylortabile-site

Taylor Tabile's personal website — plain static HTML, hosted on **Vercel**, auto-deployed from **GitHub**.

## How publishing works

Every time you `git push` to this repo, Vercel rebuilds and the live site updates in ~10–30 seconds. There is no separate "publish" step.

```
edit / add a file  →  git push  →  live
```

## Structure

```
index.html        → the homepage (served at /)
about.html etc.   → any top-level page (about.html → /about)
blog/
  index.html      → the blog listing page (/blog)
  <post>.html     → one file per post (/blog/<post>)
assets/           → shared images / css / js
```

## Add a page

1. Drop `something.html` in the root (or a subfolder).
2. `git add -A && git commit -m "Add page" && git push`
3. Live at `/something`.

## Add a blog post

1. Create `blog/my-post.html` (copy `blog/welcome.html` as a starting template).
2. Add a matching `<li>` link inside `blog/index.html`.
3. `git add -A && git commit -m "New post: my-post" && git push`

## Preview locally

Open the file directly in a browser, or from this folder run any static server, e.g.:
```
python3 -m http.server 8080   # then visit http://localhost:8080
```

## Notes

- Homepage was bootstrapped from `taylor-tabile-homepage.html`. Swap it for a different file anytime — just keep the root file named `index.html`.
- Later upgrade (Phase 2): a static site generator (Astro) can turn Markdown posts into styled HTML automatically, so publishing becomes "drop a `.md` file and push."
