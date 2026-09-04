# Agent purpose & scope — Digital Garden

This file is for any AI agent working in this repo — Claude, GPT, Gemini, a bare API loop, whatever's driving. Read this before editing anything.

## What this repo is for

A public digital garden: an Obsidian vault (`content/`) published as a website via Quartz. Real name, real face, meant to be read by strangers. That single fact should shape every decision below more than any generic "best practice" would.

## Your purpose here

- Help draft, edit, and structure posts in `content/` when asked.
- Maintain the Quartz config, build pipeline, and deploy workflow.
- Keep `PROJECT-NOTES.md` current — when you make or learn about a decision (naming, domain, tooling, structure), log it there. Don't let decisions live only in a chat transcript.
- Flag, don't silently fix, anything that looks like it crosses from "public-appropriate" into "should not be here" (see Scope below).

## Scope — what NOT to do without asking first

- **Don't publish anything third parties said in confidence** — this includes content lifted from the `sangreeal` workspace, client work, private conversations, or anyone else's unshared writing. When in doubt, treat it as private and ask.
- **Don't invent post content.** If a draft is thin, say so and ask for more material — don't pad it with fabricated specifics, invented quotes, or claims V didn't make.
- **Don't set `draft: false`** on a post unless explicitly told it's ready to publish. Default to draft.
- **Don't touch DNS, domain registration, or hosting billing** — flag what's needed and let V handle the account-level actions.
- **Don't restructure `quartz/` internals** unless the task is specifically about the build pipeline — most tasks only need `content/` and `quartz.config.yaml`.
- **No secrets in this repo.** It's public. API keys, tokens, personal addresses/phone numbers, anything sensitive — none of it belongs in a committed file here, even temporarily.

## Working conventions

- This repo is independent of `sangreeal` — don't assume shared context, tooling, or conventions from that workspace unless a human explicitly bridges them.
- Frontmatter on every post: `title`, `date`, `tags`, `draft`. See README.md for the exact block.
- Keep commit messages plain and factual — they're public history too.

## If you're not sure

Ask, or write the open question into `PROJECT-NOTES.md` under "Open questions" rather than guessing and moving on.
