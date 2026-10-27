# Basecamp API Documentation Repo

Docs-only repo — no code, no build system. `README.md` is the main guide (auth, pagination, domain model, endpoint index). `sections/` has one `.md` per API resource (~60 files).

## Sync target only — do not edit docs here

This repo is a read-only mirror of the authoritative docs in the private
`basecamp/bc3` repo at `doc/api/`. `README.md`, `CONDUCT.md`, and everything
under `sections/` is copied verbatim by bc3's `script/api/sync_to_bc3_api` —
any change made directly here will be overwritten by the next sync and will
silently diverge from the source in the meantime.

To change doc content: land the change in bc3's `doc/api/`, then run the sync
script from a bc3 checkout and commit the result here. Review feedback on doc
content should be redirected to bc3.

Only repo-local files that the sync does not copy (this file, GitHub metadata)
may be edited directly.

### Sync PRs are expected — off-target edits are not

A PR that changes `README.md`, `CONDUCT.md`, or a `sections/*.md` file **should be
a sync PR** — the verbatim output of `script/api/sync_to_bc3_api`, which is the
only sanctioned way this content changes. So a PR modifying those files is
expected and correct — review the documentation on its merits; don't flag the sync
itself as an unauthorized direct edit. A sync PR's description carries this footer:

> Synced from bc3 `doc/api/` by `script/api/sync_to_bc3_api` — not a hand-edit.

An **off-target edit** hand-changes that content on a branch, bypassing the sync:
no footer, and it won't match bc3's `doc/api/`. Those are what to redirect to bc3;
the next sync overwrites them regardless. A PR that touches only this file or
GitHub metadata is the exception — the sync doesn't copy those, so they're edited
here directly and carry no footer.

## Agent-led landing: the scheduled sync only

Landing path: `bin/bc-api-sync --apply --merge`

The scheduled docs sync may merge its own sync PR, and nothing else, by that
one path; the line above is the grant it reads. It merges only a PR it opened from the
`bc3-docs-sync` branch into `master`, squash-merged at the head it pushed, and
only when its risk check scores the sync low. Every other PR here, edits to this file
included, lands on a person's word.

**The risk check.** Before anything is pushed, every line the sync would add is
scored. A score of 5 or more is high risk, and any one of these makes it high
on its own:

- a credential shape, or a NUL byte;
- a Basecamp account URL outside the example accounts, or an email address
  outside the example domains;
- wording that says it is internal-only, confidential or unreleased, or that a
  feature is behind a flag, in beta or coming soon;
- a host that isn't public: localhost, a private network, an internal 37signals
  domain or tool;
- an endpoint whose path names something bc3's routes don't;
- a link or reference to a basecamp repository that isn't public;
- an HTML comment other than the example `<!-- START … -->` and
  `<!-- END … -->` markers.

Lower-weight signals add up and make a sync high at 5: a host these docs don't
link yet (1 each), a removed section (2 each), more than 40 files at once (1).

**High risk** pushes nothing and waits for a person, who either fixes the source
in bc3 or accepts the findings; an accepted sync's PR then waits for a person to
merge. **Low risk** opens the PR, lists the findings it scored, and merges it.

## Section file format

Every `sections/*.md` follows this structure:

1. H1 title with `=====` underline, H2 per endpoint with `-----` underline (Setext, not ATX)
2. Endpoints bullet list with anchor links: `- [Get messages](#get-messages)`
3. Endpoint description as bullet: `` * `GET /buckets/1/...` `` with prose
4. `###### Example JSON Response` then `<!-- START GET /path -->` / `<!-- END GET /path -->` wrapping `` ```json`` block
5. `###### Copy as cURL` then `` ```shell `` block using `$ACCESS_TOKEN` and `$ACCOUNT_ID` env vars
6. Write endpoints add `###### Example JSON Request` before the cURL
7. `**Required parameters**:` (bold) with inline or bulleted content, and `_Optional parameters_:` (italic) typically followed by bullet lists
8. Reference-style links at bottom: `[1]: https://...`, `[pagination]: ...`

## README.md endpoint index

Lives between `<!-- START API ENDPOINTS -->` and `<!-- END API ENDPOINTS -->`. New sections go alphabetically.

## Commit messages

Imperative verb + description + `(#PR)`: `Add API documentation for timeline endpoints (#369)`

## Constraints

- No YAML frontmatter
- Don't invent API endpoints — only document real ones
- Don't add files outside `sections/` and repo root
