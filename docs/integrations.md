# Integrations: Apify, Publora, and Pixfaro

These skills work in draft-only mode with no integration at all. Each
integration below is optional, and each one must be set up through Muse's
Secure Vault custom-connector flow. Never paste an API key or token into
chat, a skill, or a commit.

## Summary

| Layer | Service | What it unlocks | Without it |
| --- | --- | --- | --- |
| Read | Apify | Fetch a post body, comments, a user's recent comments, likers and commenters | Paste the text, thread, or list |
| Write | Publora | Publish, comment, react, reshare, schedule, edit or cancel a scheduled post | Manual copy and paste into LinkedIn |
| Image | Pixfaro | Generate or edit an illustration, render a quote card, attach it on publish | Draft the image prompt and generate it elsewhere |

There is no official LinkedIn connector in this repo, and no LinkedIn
profile fetching actor: profile optimization always starts from pasted
profile text, even after Apify is connected.

## Apify (read)

- Base API: `https://api.apify.com/v2`
- Actors, all no-cookies and public, no LinkedIn login required:
  - Post body: `apimaestro/linkedin-post-detail` (about $1 per 1,000)
  - Comments and replies: `apimaestro/linkedin-post-comments-replies-engagements-scraper-no-cookies` (about $5 per 1,000)
  - A user's recent comments: `apimaestro/linkedin-profile-comments` (about $5 per 1,000)
  - Likers and commenters: `scraping_solutions/linkedin-posts-engagers-likers-and-commenters-no-cookies` (about $5 per 1,000)
- Free tier at the time of the upstream docs: $5 per month of credit.
- Alternative read route: the Apify MCP server at the filtered URL
  `https://mcp.apify.com?actors=...` with only the four actors above.
  Use the filtered URL, not the bare MCP URL, so no other actor can be
  run or billed. See the upstream `references/mcp-read-layer.md` for the
  tool names and field mapping.

## Publora (write)

- Base API: `https://api.publora.com/api/v1`
- Auth header: `x-publora-key`
- Endpoints used upstream: `POST /create-post`, `POST /linkedin-comments`,
  `DELETE /linkedin-comments`, `POST /linkedin-reactions`,
  `POST /linkedin-reshare`, plus `GET /list-posts`, `GET /get-post`,
  `PUT /update-post/<postGroupId>`, and `DELETE /delete-post/<postGroupId>`.
- A LinkedIn platform connection id is needed to publish. Upstream resolves
  it from the account when there is exactly one LinkedIn channel; with
  several channels, pick the right one explicitly.
- Free tier at the time of the upstream docs: 15 LinkedIn posts per month.
- Safety rule for any connector built on this: draft first, show the exact
  text and target, wait for approval for that draft, then publish once.
  A scheduled post that is reconsidered should be edited or cancelled
  before it goes out; a live post can only be deleted on LinkedIn itself.

## Pixfaro (image)

- Base API: `https://api.pixfaro.com/v1`
- Key format upstream: `pf_live_...`
- Operations upstream: generate, edit by image id, list models, list
  templates, render a template, and upload a logo.
- Generated images return a hosted URL that flows into a publish call as
  a media URL. LinkedIn supports up to 10 images in one multi-image post.
- Cost guard upstream: warn when the prepaid balance drops below $1, and
  ask before using premium models, which bill materially more.

## How to connect in Muse (in order)

1. Start with draft-only skills and prove the workflow with manual
   copy and paste.
2. Add Apify first if pasting post text is the main friction.
3. Add Publora next if auto-publish or scheduling is wanted, and test
   with one scheduled draft before any live post.
4. Add Pixfaro last, only if on-brand generated images are needed;
   otherwise supply image URLs.
5. For each service, verify with a harmless read first (for example,
   list platform connections for Publora), then the exact operation
   requested, and check the result back before retrying a write.
