# CLAUDE.md

Read `AGENTS.md` in this directory before doing anything. It is the single
orientation and governance document for this repo: architecture decisions,
hard content rules, build and verification steps, and gotchas. Everything in
it applies to you.

Two rules worth repeating even here:

- `master` deploys straight to the live site in ~40 seconds. Never push
  without the owner's explicit say-so.
- Local sensitive context, if present, is in `.claude/private-context.md`
  (gitignored). Check for it before running the verification greps.
