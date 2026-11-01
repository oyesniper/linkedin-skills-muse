# Changelog

## 0.1.0 — 2026-10-31

- Initial Muse adaptation of sergebulaev/linkedin-skills v1.1.28.
- 12 specialized skills rewritten concisely for Muse, in draft-only mode.
- Shared references deduplicated into a single `shared-references/` folder.
- Added `linkedin-router` for routing the seven LinkedIn workflows.
- Added README, attribution, and an integrations plan for Apify, Publora,
  and Pixfaro. No connector or credential is included.

## 0.2.0 — 2026-10-31

- Restored the full upstream method text at the user's request, replacing
  the concise 0.1.0 rewrites. Each SKILL.md now contains the complete
  upstream body, with only a short Muse adaptation header on top and
  shared-reference paths adjusted to `shared-references/`.
- Removed the `linkedin-router` skill added in 0.1.0, so this repo now
  matches the upstream 12-skill set exactly in count and method.
