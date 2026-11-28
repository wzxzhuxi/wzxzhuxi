---
name: profile-readme
description: Edit and verify this GitHub profile README safely — layout structure, self-hosted images, GitHub HTML restrictions, and a safe-edit checklist. Use when modifying README.md in this repo.
---

# Profile README editing guide

## Layout (top to bottom)

1. Centered header: an `<h1>` wrapping the `<picture>` animated header image `profile/header-{dark,light}.svg` (alt text `Hello, friend.`) — the E Corp diamond mark spins on the left, the glitching `HELLO, FRIEND.` wordmark sits on the right. Do not re-add a plain-text heading or separate badge.
2. Stats card floated right: `<img align="right" width="400" src="./profile/stats.svg" alt="GitHub Stats" />` placed just before the About Me heading so the card's bottom aligns with the last bullet line.
3. `### About Me` — plain bullet list, no emoji icons.

Keep the README minimal: no separators, extra badges, banners, or additional sections.

## Images

- `profile/header-dark.svg` and `profile/header-light.svg` — hand-authored animated header: the E Corp diamond E mark (bold E rotated 45°) spins around its vertical axis like a 3D plaque (3s per turn) beside the monospace `HELLO, FRIEND.` wordmark with RGB split and periodic character-scramble bursts. Pure SVG + CSS animation, no scripts; keep both versions in sync and respect `prefers-reduced-motion`.
- `profile/stats.svg` — self-hosted stats card regenerated daily by `.github/workflows/readme-stats.yml` (theme tokyonight, hide_border, count_private) with 30 units of transparent top padding added by the workflow so the floated card's bottom aligns with the last About Me line. Never edit it by hand; change card options in the workflow instead.
- No other image assets or external badge services.

## GitHub HTML rules

- Allowed and in use: `div`, `h1`, `picture`, `source`, `img`. Keep `<img ... />` self-closed.
- Never add `script`, `style`, `iframe`, `form`, or `on*` handler attributes — GitHub sanitizes them away.
- Every opening tag needs a closing tag. Malformed HTML silently breaks the rendered profile page.

## Safe-edit checklist

1. Read `README.md` before editing.
2. Make minimal edits; preserve personal statements verbatim.
3. Run `npx --yes markdownlint-cli2@0.24.1 README.md`; it must pass.
4. Run `git diff -- README.md` and confirm `<div>` tags remain balanced.
5. For logo changes, preview with headless Chromium, e.g. `chromium --headless --no-sandbox --default-background-color=00000000 --window-size=240,240 --screenshot=/tmp/logo.png profile/logo-dark.svg`.
6. Preview the rendered page on GitHub after pushing.
7. Commit only when asked, using `git -c user.name="zhuxi" -c user.email="156671260+wzxzhuxi@users.noreply.github.com" commit -m "..."` with a short imperative message; push to `main` only when asked.
8. Do not touch `origin/blog` unless explicitly asked.