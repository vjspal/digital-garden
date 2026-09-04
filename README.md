# Digital Garden

V's public digital garden — an Obsidian vault published as a website via [Quartz](https://quartz.jzhao.xyz). This is a separate, standalone repo from the `sangreeal` workspace (the private, agent-agnostic client/project instructions repo) — this one is public-facing, and its whole point is to be read by other people.

## What this is (and isn't)

- **Is:** learning-in-public notes, essays, and short posts — mostly the AI/tech career-transition work, published in Markdown, edited in Obsidian.
- **Isn't:** client work, internal process docs, or anything with a name/detail that isn't meant to be public. If it shouldn't be read by a stranger, it doesn't belong in `content/`.

## Layout

- `content/` — **this is the Obsidian vault.** Open this folder directly as a vault in Obsidian. Every Markdown file here becomes a page on the published site once it's out of draft.
- `content/_inbox/` — rough drafts and half-finished notes. Not linked from the site nav, not published (see Drafts below), but tracked in git so nothing gets lost.
- `quartz/`, `quartz.config.yaml` — the site generator and its configuration. You generally won't touch `quartz/` itself; `quartz.config.yaml` is where site title, theme, and plugins are configured.
- `PROJECT-NOTES.md` — running decision log for this repo (naming, tooling, domain, open questions). Read this before assuming a decision was never made — check here first.
- `AGENTS.md` — purpose and scope for any AI agent (Claude or otherwise) working in this repo.

## Publishing a post

1. Write in `content/` (or draft first in `content/_inbox/`, then move it up when it's ready).
2. Give it frontmatter:
   ```md
   ---
   title: Your Title
   date: 2026-09-03
   tags:
     - learning-in-public
   draft: false
   ---
   ```
3. `draft: true` keeps a page out of the published build entirely — use it for anything not ready for strangers to read.
4. Commit and push. The GitHub Actions workflow (once set up — see PROJECT-NOTES.md) rebuilds and deploys the site automatically.

## Local preview

```bash
npm ci
npx quartz build --serve
```

Opens a local preview at `http://localhost:8080`. First run may take a minute — Quartz fetches its theme/plugin packages on first build.

## Status

Scaffolded 2026-09-03: Quartz (obsidian template) initialized, config in place, builds clean with a placeholder home page. Domain and GitHub Pages/Actions deploy are **not yet wired** — see PROJECT-NOTES.md for what's still open before this is actually live.
