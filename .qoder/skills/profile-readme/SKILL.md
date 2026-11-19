---
name: profile-readme
description: Edit and verify this GitHub profile README safely — layout structure, badge services, GitHub HTML restrictions, and a safe-edit checklist. Use when modifying README.md in this repo.
---

# Profile README editing guide

## Layout (top to bottom)

1. Centered intro: `<div align="center">` containing the H1 `👋 Hi, I'm zhuxi (老王)` and the self-hosted stats card `./profile/stats.svg`.
2. `---` separator, then a right-floated top-languages card (`align="right"`, `width="400"`).
3. `### 🚀 About Me` — emoji bullet list, closed with `<br clear="right"/>`.
4. `## 📊 GitHub Statistics` — two-cell table with a stats card and a streak card, then a centered activity-graph badge.
5. Centered quote footer (Linus Torvalds). Sections are separated by `---`.

## Images and badge services

- `profile/stats.svg` — self-hosted stats card, regenerated daily by `.github/workflows/readme-stats.yml`; never edit by hand.
- The remaining hosts are external services (custom deployments, not upstream defaults) — keep exact hostnames:
- `github-readme-stats-fast.vercel.app` — top languages
- `github-readme-stats-eight-theta.vercel.app` — GitHub stats card
- `github-readme-streak-stats-nine-roan.vercel.app` — streak stats
- `github-readme-activity-graph.vercel.app` — activity graph

Common params: `theme=tokyonight` (or `tokyo-night` for the graph), `hide_border=true`, `count_private=true`.

## GitHub HTML rules

- Allowed and in use: `div`, `img`, `table`, `tr`, `td`, `a`, `br`. Keep `<img ... />` self-closed.
- Never add `script`, `style`, `iframe`, `form`, or `on*` handler attributes — GitHub sanitizes them away.
- Every opening tag needs a closing tag. Malformed HTML silently breaks the rendered profile page.

## Safe-edit checklist

1. Read `README.md` before editing.
2. Make minimal edits; preserve personal statements verbatim.
3. Run `npx --yes markdownlint-cli2@0.24.1 README.md`; it must pass.
4. Run `git diff -- README.md` and confirm `<div>`/`<table>` tags remain balanced.
5. Preview the rendered page on GitHub after pushing — third-party badge services can fail independently of your edit.
6. Commit only when asked, using `git -c user.name="zhuxi" -c user.email="156671260+wzxzhuxi@users.noreply.github.com" commit -m "..."` with a short imperative message; push to `main` only when asked.
7. Do not touch `origin/blog` unless explicitly asked.
