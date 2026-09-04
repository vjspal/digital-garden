# Project notes — Digital Garden

Running decision log. Check here before assuming something wasn't decided.

## What this is

Started 2026-09-03. A public digital garden — Obsidian vault, published via Quartz — separate from the `sangreeal` workspace on purpose (see "Why not inside sangreeal" below). First content: two draft posts V already has, submitted after this scaffold existed.

## Decisions made

- **Tool: Quartz**, not the Obsidian "Digital Garden" community plugin. Chosen for durability/control (self-hosted build, not tied to Netlify) — V didn't override this default when asked, so treat it as decided, not tentative.
- **Repo name: `digital-garden`**, GitHub account `vjspal`. Cheap to rename later if it doesn't stick.
- **Template: `obsidian`** (Quartz's built-in template) — full Obsidian-flavored-markdown support (wikilinks, callouts, embeds), shortest-link resolution.
- **Location: nested inside `X:\sangreeal\digital-garden`**, but as its own independent git repo — not part of sangreeal's git history, not using sangreeal's 11-folder client/project taxonomy. See below for why this needed a second look.
- **Domain: registered, DNS access not yet confirmed.** Wiring the custom domain (CNAME, GitHub Pages/hosting DNS records) is explicitly deferred — `quartz.config.yaml`'s `baseUrl` is currently a placeholder (`changeme.example.com`) and must be updated once the real domain + DNS access are confirmed.

## Why not inside sangreeal's `projects/`

`sangreeal/_meta/consolidation-decisions.md` (written the same day this repo was started) explicitly excluded a personal Obsidian vault (`yggdrasil`, V's private journal) from sangreeal, on the grounds that sangreeal "stays scoped to client/project knowledge." A public digital garden isn't the same thing as that private journal, but it's also not client/project knowledge — it doesn't fit the 11 functional folders (`web-ops`, `brand-identity`, etc.) that every `projects/*` entry uses. So this repo sits as a sibling to `_meta` and `projects/` inside the sangreeal folder — filesystem-adjacent for convenience, but a fully separate git repo and GitHub remote. Worth a second look if that reasoning doesn't hold up in practice.

## Open questions / not yet done

- **GitHub repo not yet created.** The GitHub MCP plugin available to this session isn't authenticated, and the built-in browser isn't signed into GitHub — neither could create/push the repo. Options: (a) V signs into GitHub in the browser pane and an agent drives repo creation from there, (b) V provides a PAT for the GitHub plugin, (c) V publishes this folder via GitHub Desktop, same as was just done for `sangreeal`.
- **Stray broken folder.** An earlier attempt to `git clone` directly onto the mounted `X:\sangreeal` drive left a partial, permission-locked `.git` folder inside what's now this repo's location — the sandboxed agent couldn't delete it (device delete permission was denied by the auto-mode classifier). V needs to delete it manually before treating the delivered files as the final on-disk copy, or the delivered content should be unpacked into a differently-named folder instead.
- **GitHub Pages / Actions deploy** — Quartz ships a default GitHub Actions workflow; needs enabling in repo settings once the repo exists on GitHub.
- **Domain DNS access** — confirm who/where DNS is managed before wiring the custom domain.
- **The two draft posts** — not yet in `content/`. Submit them and they'll go into `content/` (or `content/_inbox/` first if they need editing).
- **Site title/theme** — `pageTitle` is currently a placeholder ("V — Digital Garden"); colors/fonts are Quartz defaults. Cosmetic, low priority until there's real content to look at.

## 2026-09-03 — hosting decision

**Hosting: Cloudflare Pages**, not GitHub Pages (Quartz's default). V's domain and DNS are already on Cloudflare, so one dashboard handles both instead of two. Consequences:
- `quartz.config.yaml`'s `baseUrl` still needs updating from the `changeme.example.com` placeholder to the real domain once it's attached in Cloudflare.
- The GitHub Actions workflows Quartz ships (`.github/workflows/*.yaml` - `deploy-v5.yaml` especially) target GitHub Pages and aren't needed. Left in place for now; safe to delete once Cloudflare Pages is confirmed working, to stop confusing failed-run notifications.
- Cloudflare Pages build settings needed: build command `npm ci && npx quartz build`, output directory `public`, `NODE_VERSION` environment variable set to `22` (Quartz requires Node 22+, Cloudflare's default may be older).
- The GitHub PAT V generated earlier was for a different problem (letting the cloud sandbox create/push the repo directly) and turned out to be a dead end - this sandbox's network proxy only allows pre-configured repos, no token fixes that. Not needed for Cloudflare Pages setup at all, which is dashboard/OAuth-based.
