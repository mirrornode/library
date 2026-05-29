# MIRRORNODE Library

Shared reference archive for MIRRORNODE project code, audits, repo maps, and implementation receipts.

This repo is the index layer for project reality. It should answer:

- What code surfaces exist?
- Which repo owns each surface?
- What is real versus partial, speculative, blocked, or archived?
- What evidence proves current state?
- What should be touched next?
- What should not be touched?

## Start here

- [`MIRRORNODE_PROJECT_CODE_LIBRARY.md`](./MIRRORNODE_PROJECT_CODE_LIBRARY.md) — full current code library and project surface map.
- `audits/osiris/` — Osiris-related audit references.
- `audits/trees/` — repository tree/audit snapshots.

## Process

Every new shared document should include:

```txt
DATE:
SOURCE:
TARGET:
REPO:
BRANCH / PR:
WHAT CHANGED:
WHAT IS VERIFIED:
WHAT IS NOT VERIFIED:
NEXT ACTION:
BLOCKERS:
DO NOT TOUCH:
RECEIPT NEEDED:
```

## Status labels

| Status | Meaning |
|---|---|
| `REAL` | Exists in code and has a receipt. |
| `PARTIAL` | Exists, but not fully wired or verified. |
| `SPEC` | Described but not implemented. |
| `BLOCKED` | A specific blocker prevents completion. |
| `ARCHIVE` | Keep for reference; do not actively build from it. |

## Rule

Do not promote conversation claims into project reality without a receipt: file path, PR, commit, CI run, route response, deployment URL, terminal output, or audit artifact.

## Current priority

1. Keep `mirrornode-platform` commerce work separate from Osiris/FastAPI verdict-stream work.
2. Merge health stubs before Stripe commerce.
3. Save future shared state here instead of scattering it across chats.
