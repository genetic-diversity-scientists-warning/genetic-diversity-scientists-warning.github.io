# Website — Scientists' Warning on Genetic Diversity Loss

Public-facing site for the consensus paper. Built with [Hugo](https://gohugo.io).

This source lives in the **private** workspace. It is not in the shared drive
because co-authors don't need to edit it — only the manuscript, colabs, and
clean data go there.

## Quick start

```bash
# install hugo (one-time, if not already)
brew install hugo

# preview locally — http://localhost:1313
hugo server -D

# build the static site to ./public
hugo
```

## Layout

```
hugo.toml             # site config, menu, params
content/
  _index.md           # home page intro paragraph
  documents.md        # manuscript + Google Doc links (placeholder URLs)
  authors.md          # author policy
  about.md            # about the Delphi process
  news/               # press releases + announcements (one .md per post)
archetypes/news.md    # template used by `hugo new news/<slug>.md`
layouts/              # custom HTML templates (no theme dependency)
assets/css/main.css   # styling
static/img/           # favicon + future images
```

## Common tasks

### Add a press release

```bash
hugo new news/2026-06-01-some-slug.md
```

Edit the resulting file in `content/news/`. The home page and the
News & press index will pick it up automatically (sorted by date desc).

### Update the Google Doc links

Edit `content/documents.md` and replace the placeholder `href="#"` values
with the real Google Doc URLs. Same for the author sign-up sheet.

### Change site metadata (title, journal, contact)

Edit the `[params]` block in `hugo.toml`. The header, footer, and meta tags
will update.

## Deploy

The built site is a plain `public/` folder. Drop it on any static host:

- **GitHub Pages** — push the repo, point Pages at `/public` (or use the
  `hugo-deploy` action).
- **Netlify** — `hugo` as build command, `public` as publish directory.
- **Cloudflare Pages** — same build/publish settings as Netlify.
- **Lab server / S3 / etc.** — `rsync -av public/ user@host:/var/www/...`

No domain yet. When picking one, common patterns:

- `geneticdiversityloss.org`
- `scientistswarning.org/genetic-diversity`
- A subpath of a lab page

Set `baseURL` in `hugo.toml` accordingly before building.
