---
name: profile-readme
description: Edit and verify this GitHub profile README safely — layout structure, self-hosted stats card, GitHub HTML restrictions, and a safe-edit checklist. Use when modifying README.md in this repo.
---

# Profile README editing guide

## Layout (top to bottom)

1. Centered header: `<div align="center">` containing the H1 `👋 Hi, I'm zhuxi (老王)`.
2. Stats card floated right: `<img align="right" width="400" src="./profile/stats.svg" alt="GitHub Stats" />` placed just above the About Me heading so it sits on the same row as the list.
3. `### 🚀 About Me` — emoji bullet list.

Keep the README minimal: these are the only two sections, with no separators or other badges.

## Images

- `profile/stats.svg` is the only image — a self-hosted stats card regenerated daily by `.github/workflows/readme-stats.yml` (theme tokyonight, hide_border, count_private). Never edit it by hand; change card options in the workflow instead.
- No external badge services are used.

## GitHub HTML rules

- Allowed and in use: `div`, `img`, `br`. Keep `<img ... />` self-closed.
- Never add `script`, `style`, `iframe`, `form`, or `on*` handler attributes — GitHub sanitizes them away.
- Every opening tag needs a closing tag. Malformed HTML silently breaks the rendered profile page.

## Safe-edit checklist

1. Read `README.md` before editing.
2. Make minimal edits; preserve personal statements verbatim.
3. Run `npx --yes markdownlint-cli2@0.24.1 README.md`; it must pass.
4. Run `git diff -- README.md` and confirm `<div>` tags remain balanced.
5. Preview the rendered page on GitHub after pushing.
6. Commit only when asked, using `git -c user.name="zhuxi" -c user.email="156671260+wzxzhuxi@users.noreply.github.com" commit -m "..."` with a short imperative message; push to `main` only when asked.
7. Do not touch `origin/blog` unless explicitly asked.
