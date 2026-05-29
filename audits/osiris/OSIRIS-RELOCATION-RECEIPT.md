# OSIRIS RELOCATION RECEIPT

```text
DATE:             2026-05-29
SOURCE:           mirrornode-platform / app/osiris/
TARGET:           mirrornode-osiris (DOES NOT EXIST)
REPO:             mirrornode/mirrornode-platform
BRANCH / PR:      NONE — blocked, no action taken
WHAT CHANGED:     NOTHING — deletion withheld pending preservation
WHAT IS VERIFIED: app/osiris/ is confirmed present in mirrornode-platform main
                  Files inventoried: main.py, rotan_routes.py, pyproject.toml,
                  poetry.lock, __pycache__/ (compiled), venv/ (local only)
WHAT IS NOT       venv/ contents not pushed to GitHub (correctly)
VERIFIED:         No audit of pyproject.toml dependencies against poetry.lock
                  rotan_routes.py uses SUPABASE_SERVICE_KEY (wrong key name,
                  should be SUPABASE_SERVICE_ROLE_KEY — NOT fixed in this pass)
NEXT ACTION:      1. Create mirrornode-osiris repo
                  2. Push main.py and rotan_routes.py to mirrornode-osiris main
                  3. Write REAL preservation receipt
                  4. Open PR C in mirrornode-platform removing app/osiris/ only
BLOCKERS:         mirrornode-osiris repo does not exist (GitHub 404 confirmed)
                  Cannot delete from source without preservation target
DO NOT TOUCH:     PR #5 (feat/health-stubs)
                  PR #6 (feat/stripe-commerce)
                  Stripe corridor
                  Health routes
                  FastAPI logic beyond relocation
                  Any new architecture
RECEIPT NEEDED:   Yes — this document is the BLOCKED receipt
                  A REAL receipt must replace this after preservation completes
STATUS:           BLOCKED
```

---

## Inventoried files in `mirrornode-platform/app/osiris/`

| File | SHA (GitHub main) | Notes |
|------|-------------------|-------|
| `main.py` | `b2f82ab18394e3f17e941ad4b6ea0a7c4412f38f` | FastAPI app, WebSocket `/ws/ptah/verdicts`, mock verdict broadcaster, hardcoded `host="0.0.0.1"` (typo, should be `0.0.0.0`) |
| `rotan_routes.py` | `da53a8a48b90580a8caf9599876dcc32f04b14cc` | APIRouter `/rotan-q`, Merkle chain ledger, Supabase write, bearer auth via `ROTAN_DEV_KEY`. Uses wrong env key `SUPABASE_SERVICE_KEY` — do not fix during relocation pass |
| `pyproject.toml` | `e4c6065f0cfd97960669e9e9e98799c710d114aa` | Poetry project config |
| `poetry.lock` | `20bb410251be44ffd789ff2e7c107c7f34ed1679` | Dependency lock including FastAPI |
| `page.tsx` | `18f7443696a87d19ffb56f9f49b0878b9f7d3ba8` | Next.js UI page — stays in mirrornode-platform |
| `__pycache__/` | — | Compiled bytecode — do not copy to mirrornode-osiris |
| `venv/` | — | Local only, not pushed to GitHub — do not copy |

**Files to move to `mirrornode-osiris`:** `main.py`, `rotan_routes.py`, `pyproject.toml`, `poetry.lock`  
**Files to leave in `mirrornode-platform`:** `page.tsx`  
**Files to discard:** `__pycache__/`, `venv/`

---

## Known issues in the Osiris surface (do not fix during relocation pass)

- `rotan_routes.py` line 10: `os.environ["SUPABASE_SERVICE_KEY"]` — wrong key name, should be `SUPABASE_SERVICE_ROLE_KEY`
- `main.py` line last: `host="0.0.0.1"` — typo, should be `0.0.0.0`
- Verdict data in `main.py` is entirely randomized mock data — no real audit logic

These are **logged here only**. Fix them in a separate Osiris pass after relocation.

---

## Completion criteria to upgrade STATUS from BLOCKED → REAL

1. `mirrornode-osiris` repo created
2. `main.py`, `rotan_routes.py`, `pyproject.toml`, `poetry.lock` committed to `mirrornode-osiris/main`
3. This receipt updated with preservation commit SHA
4. PR C opened in `mirrornode-platform` removing `app/osiris/` (excluding `page.tsx`)
5. PR C description references preservation commit
