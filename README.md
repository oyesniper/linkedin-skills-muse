# LinkedIn Skills for Muse

Muse-native LinkedIn skills for drafting, planning, auditing, and
publishing LinkedIn content — with the full upstream method and a
draft-first approval workflow.

This is an adaptation of the upstream bundle
[sergebulaev/linkedin-skills](https://github.com/sergebulaev/linkedin-skills)
(v1.1.28, MIT). It is not affiliated with, or a replacement for, the upstream
project. Upstream remains the source for the full Claude Code / Codex method;
this repo optimizes that method for Muse.

## What is in here

- 12 specialized skills, with the full upstream method text
- Shared references in one place, instead of a copy inside every skill
- Draft-only by default: every draft is shown in chat and needs explicit
  approval before any publish, comment, reaction, reshare, or scheduled post

```
skills/
  linkedin-post-writer/       # New posts, hooks, founder angles
  linkedin-content-planner/   # 7-day content plans
  linkedin-profile-optimizer/ # Headline, About, Featured, Experience, Skills
  linkedin-comment-drafter/   # Top-level comments and reshares
  linkedin-reply-handler/     # Replies and whole-thread sweeps
  linkedin-thread-monitor/    # Author replies and the warm follow-up window
  linkedin-engager-analytics/ # Likers and commenters grouped by ICP fit
  linkedin-hook-extractor/    # Hook formula from a viral post
  linkedin-humanizer/         # Remove AI tells, audit before publishing
  linkedin-interviewer/       # Story Bank: roles, numbers, turning points
  linkedin-repurposer/        # Other-platform content into a native post
  linkedin-employee-advocacy/ # Team advocacy programs
shared-references/            # Hook formulas, voice rules, founder topics, etc.
docs/
  integrations.md             # Apify, Publora, and Pixfaro integration plan
```

## The seven workflows

| Workflow | Start with |
| --- | --- |
| Post writing | `linkedin-post-writer`, then `linkedin-humanizer` |
| Content planning | `linkedin-content-planner` |
| Profile optimization | `linkedin-profile-optimizer` |
| Comment drafting | `linkedin-comment-drafter` or `linkedin-reply-handler` |
| Engagement analysis | `linkedin-engager-analytics` or `linkedin-thread-monitor` |
| Content repurposing | `linkedin-repurposer`, then `linkedin-humanizer` |
| Publishing workflows | Draft first, manual copy and paste until a connector is set up |

If you do not know which skill to use, start with the workflow table above.

## Install in Muse

Copy the skill folders you want into your Muse custom-skills folder:

```bash
cp -r skills/linkedin-post-writer skills/linkedin-humanizer \
  ~/workspace/custom-skills/
```

Keep `shared-references/` reachable at the same relative layout, or update the
`../../shared-references/` links in each `SKILL.md` to match where you put it.
Each skill has a `skill.yaml` beside its `SKILL.md`. Specialized skills
are discoverable by search in Muse.

## Important limits

- **Profile reviews need pasted text.** There is no LinkedIn profile
  fetching actor in the upstream read layer, so a profile URL alone cannot
  be fetched. Paste the headline, About, Experience, Skills, and custom URL.
  A section you have not shown is never scored or rewritten.
- **Reading posts, comments, and engagers needs Apify.** Without it, paste
  the post text, comment thread, or engager list. See `docs/integrations.md`.
- **Publishing needs Publora or a manual step.** Without it, publishing is
  manual copy and paste into LinkedIn.
- **Images need Pixfaro or a supplied image URL.** Without it, a skill
  drafts the image prompt for you to generate elsewhere.
- **No secrets in this repo.** Never put an API key, token, or password in
  a skill, a doc, a script, or a commit. Connectors in Muse must use the
  Secure Vault flow.

## Workflow rules

1. Draft in chat.
2. Show the full draft and its target.
3. Wait for explicit approval for that exact draft.
4. Only then publish, comment, react, reshare, or schedule.
5. Never reuse an approval given for a different draft.
6. Never invent a number, client name, result, or profile section.

## Attribution

See [ATTRIBUTION.md](ATTRIBUTION.md) for what came from upstream, what was
changed for Muse, and what was added here. The upstream MIT license is kept
in [LICENSE](LICENSE).

## Changelog

See [CHANGELOG.md](CHANGELOG.md).
