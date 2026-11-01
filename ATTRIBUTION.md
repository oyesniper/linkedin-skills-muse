# Attribution

## Upstream

This repository adapts
[sergebulaev/linkedin-skills](https://github.com/sergebulaev/linkedin-skills),
version 1.1.28, by Sergey Bulaev, licensed under MIT (see `LICENSE`).

Upstream provides the original 12 skills, their hook formulas, templates,
checklists, and reference material, plus the Apify read layer, Publora write
layer, and Pixfaro image layer described in `docs/integrations.md`.

## What was changed for Muse

- Each upstream `SKILL.md` is kept in full. The only Muse additions are a
  short adaptation header on top (draft-only mode, approval before any
  publish, paste fallback, no secrets in chat), a `skill.yaml` beside each
  `SKILL.md` carrying the frontmatter metadata, and shared-reference paths
  adjusted to `shared-references/`.
- The 11 shared root references live once in `shared-references/`,
  instead of a copy inside every skill.
- Muse-unused helper scripts were removed.
- All skills are draft-only by default in this repo. No connector, API key,
  or token is included or required to use the drafting skills.
- Note: a concise 0.1.0 rewrite and a `linkedin-router` skill existed
  briefly and were removed in 0.2.0 at the user's request for the exact
  upstream version. The concise version is kept locally as a backup only
  and is not in this repo.

## What was not changed

- The upstream method, formulas, templates, and checklists are preserved
  through the local and shared references.
- No upstream code is executed by these skills. The upstream Python
  library (`lib/`) and scripts are not included here; see
  `docs/integrations.md` for how a Muse custom connector would replace
  that execution layer if you choose to connect Apify, Publora, or Pixfaro.
