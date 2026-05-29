# MIRRORNODE Project Code Library

**Date:** 2026-05-29  
**Purpose:** One practical index of the project code surfaces we have worked on, with current role, reality status, key files/routes, and next action.  
**Scope:** GitHub-accessible MIRRORNODE repositories, recent conversation artifacts, and currently active development tracks.  
**Rule:** This is a library/index, not a canon lock. Promote entries to canon only after verification receipts exist.

---

## 0. Operating Rule

Every code surface should be classified by:

| Field | Meaning |
|---|---|
| Repo / surface | Where the code actually lives |
| Role | What the surface is responsible for |
| Status | Active, partial, support, prototype, archive, or unknown |
| Evidence | README, package config, routes, tests, PRs, logs, deployment, or artifact |
| Next action | The one useful move to make it more real |

No concept should be treated as real unless it has a file, route, test, commit, deployment, log, or artifact proving it.

---

## 1. Active Command Surfaces

### 1.1 `mirrornode/mirrornode-platform`

**Role:** Primary Next.js commercial/platform frontend.  
**Runtime:** Next.js, React, TypeScript, Vercel.  
**Status:** Active / revenue-critical.

**Verified code facts:**
- Package name: `mirrornode-platform`.
- Node engine: `20.x`.
- Scripts: `dev`, `build`, `start`, `lint`, `test`.
- Dependencies include: Next, React, Stripe, OpenAI, Pinecone, Zod, pdf-parse.
- Current env guard hard-throws on `AGENT_BASE_URL`, `ROTAN_DEV_KEY`, `SUPABASE_URL`, and `SUPABASE_SERVICE_KEY`.
- `.env.example` still uses `SUPABASE_SERVICE_KEY`; recent correction track requires `SUPABASE_SERVICE_ROLE_KEY`.

**Known tracks:**
- Osiris Audit payment link / Stripe commerce.
- Health stubs.
- Situation Room / agents UI.
- `/api/agents`, `/agents`, `/osiris`, `/audit`.
- Scoped env guards.
- Stripe checkout/webhook PR.

**Library status:** `ACTIVE — PLATFORM / COMMERCE / PUBLIC SURFACE`

**Next action:**
1. Push health stubs first.
2. Correct env split.
3. Correct Stripe route implementation.
4. Keep FastAPI/verdict-stream out of this repo.

---

### 1.2 `mirrornode/mirrornode-backend`

**Role:** Backend runtime / system-contract surface.  
**Runtime:** Python/FastAPI direction, serverless/Vercel-adjacent deployment history.  
**Status:** Active but must be reality-checked route by route.

**Verified code facts:**
- `SYSTEM_CONTRACT.md` identifies MIRRORNODE ground truth version 1.1 as of 2026-04-28.
- Real entry point named there: `POST /dispatch`.
- Lattice truth surfaces named there: `/manifest`, `/lattice/status`, `/health`, `/heartbeat`, `/identity`.
- Audit mechanism: `emit_audit(repo, event_type, actor, verdict, evidence)`.
- Explicit non-claims: `/system/execute`, `/system/replay`, and `/execute-task` are not real routes.
- `AGENTS_TODO.md` says execution should route through LUCIAN `POST /dispatch`, health surfaces should be honest, and non-existent endpoints should not be documented.
- OSIRIS in the backend contract is payment/commerce focused and should maintain `/health`, `/heartbeat`, `/identity`, and `/stripe/status`.

**Library status:** `ACTIVE — BACKEND / CONTRACT / RUNTIME TRUTH`

**Next action:**
- Confirm actual files implementing `/dispatch`, `/health`, `/manifest`, `/lattice/status`, `/heartbeat`, `/identity`.
- Remove or quarantine any docs that imply routes the contract marks as non-real.

---

### 1.3 `mirrornode/MIRRORNODE-CORE-HUB`

**Role:** Canonical docs, schemas, coordination, governance.  
**Runtime:** Documentation/control plane; not the commercial runtime.  
**Status:** Active support / governance-critical.

**Verified code facts:**
- README calls it the central coordination hub.
- README describes a manifest-driven agent lattice.
- README points to `lib/agents.ts` as a single source of truth for the agent manifest.
- README describes `/api/agents` and `/api/agents/[id]` as manifest routes.
- README defines Osiris as a constrained static audit engine, not a compliance certification tool, penetration test platform, CVE database, or monitoring service.
- Repo structure includes `schemas/`, `examples/`, `canon/`, `protocols/`, and `state/`.
- Status section references RISING_STAR v1.1.2, 6 active agents, and Osiris schema v1.0.0.

**Known tracks:**
- Canon Gate.
- Librarian / Judge.
- Hermes Test Harness.
- Security Mesh.
- Epistemic Boundary.
- Claim class enforcement.

**Library status:** `ACTIVE — GOVERNANCE / CANON / SCHEMAS`

**Next action:**
- Add or update a `CODE_LIBRARY.md` or `docs/CODE_LIBRARY.md`.
- Keep this repo as the source of structure and rules, not as the place where every runtime lives.

---

### 1.4 `mirrornode/mirrornode`

**Role:** Canonical monorepo / orchestration system.  
**Runtime:** TypeScript monorepo with workspaces.  
**Status:** Active but mixed with older claims; use carefully.

**Verified code facts:**
- Package name: `mirrornode-monorepo`.
- Workspaces: `cores/*`, `agents/*`, `starter-kits/*`, `services/*`.
- Scripts: `build`, `test`, `build:cores`, `test:cores`, `smoke:theia`.
- README describes core layers:
  - `cores/mirrornode-core` as shared brain.
  - `cores/theia-core` as gateway.
  - `agents/*` as first-class nodes.
  - `starter-kits/*` as dashboard/agent/game templates.
- README references production surfaces including MIRRORNODE Public HUD and Osiris Operator Console.
- README describes Python bridge local dev at port 8420.
- README says Bridge is in progress and mission checklist includes bridge loop, HUD actions, inventory codes, GitHub/Vercel deployment, and ops docs.

**Library status:** `ACTIVE — MONOREPO / CORE / AGENTS / STARTER KITS`

**Next action:**
- Audit actual workspace folders and verify which packages still build.
- Treat README claims as directional until matched by files/tests.

---

### 1.5 `mirrornode/mirrornode-py`

**Role:** Python/FastAPI event hub / Hermes bridge.  
**Runtime:** Python, FastAPI.  
**Status:** Active support / bridge track.

**Verified code facts:**
- README title: `MIRRORNODE Python Bridge v0.2.0 (Hermes)`.
- Described as a FastAPI event hub for MIRRORNODE distributed AI lattice.
- Structure: `core/`, `tests/`, `scripts/`.

**Known tracks:**
- Event hub.
- Bridge service.
- Hermes transport.
- `/event` and health-style status routes depending on implementation.

**Library status:** `SUPPORT — PYTHON BRIDGE / EVENT HUB`

**Next action:**
- Verify routes and tests directly from source.
- Align with `mirrornode-backend` so there are not two competing backend truths.

---

## 2. Osiris Surfaces

### 2.1 `mirrornode/osiris`

**Role:** Osiris Operator Console / Vite UI surface.  
**Runtime:** Vite, React.  
**Status:** Active UI/prototype.

**Verified code facts:**
- Package name: `osiris`.
- Scripts: `dev`, `build`, `lint`, `preview`.
- Dependencies include React 19, lucide-react, Vite.

**Known tracks:**
- Operator console.
- HUD components.
- Osiris audit/status display.
- Vercel front-end surface.

**Library status:** `ACTIVE / PROTOTYPE — OSIRIS UI CONSOLE`

**Next action:**
- Separate UI shell from payment/backend authority.
- Verify whether `/api/osiris/audit` lives here or elsewhere.

---

### 2.2 `mirrornode/osiris-ui`

**Role:** Earlier / alternate Osiris Next.js UI.  
**Runtime:** Next.js 14, React 18.  
**Status:** Support or legacy UI.

**Verified code facts:**
- Package name: `osiris-ui`.
- Scripts: `dev`, `build`, `start`.
- Dependencies: Next 14, React 18.
- TypeScript present.

**Library status:** `SUPPORT / POSSIBLE LEGACY — OSIRIS UI`

**Next action:**
- Decide if this is still active or superseded by `mirrornode/osiris` and `mirrornode-platform`.

---

### 2.3 `mirrornode/osiris-audit`

**Role:** Intended Osiris audit/tooling repo, but current README appears scaffold-like.  
**Runtime:** Minimal Node/container scaffold in current README.  
**Status:** Needs review; likely scaffold or misnamed baseline.

**Verified code facts:**
- README title says `mirrornode-core (scaffold)`.
- README says the repository was empty and received a small CI/container scaffold.
- Current described files: `app/`, `Dockerfile`, `.dockerignore`, `docker-compose.yml`, GitHub workflows.
- README local path references `/Users/morningstar/-mirrornode-core`, suggesting possible copy/paste or repo-role mismatch.

**Library status:** `UNCLEAR — AUDIT NAME / SCAFFOLD CONTENT`

**Next action:**
- Inspect actual tree.
- Decide whether to archive, repurpose, or rebuild as true Osiris audit tooling.
- Do not treat this as production audit code without more evidence.

---

### 2.4 Local `mirrornode-osiris`

**Role:** Mentioned as separate local repo/surface for FastAPI verdict stream / Osiris backend.  
**Runtime:** Local/Vercel project surface according to recent handoff.  
**Status:** Important but not fully verified from GitHub list in this pass.

**Known current rule:**
- Stripe work belongs in `mirrornode-platform`.
- FastAPI `main.py` and verdict stream belong outside the platform surface.

**Library status:** `ACTIVE LOCAL TRACK — NEED GITHUB/REMOTE CONFIRMATION`

**Next action:**
- Run local repo inventory:
  ```bash
  cd /Users/platform/code/mirrornode/mirrornode-osiris
  git remote -v
  find . -maxdepth 3 -type f | sort
  ```

---

## 3. Theia / Gateway Surfaces

### 3.1 `mirrornode/theia-core`

**Role:** Theia gateway/core surface.  
**Runtime:** CommonJS Node server.  
**Status:** Small active/supporting runtime.

**Verified code facts:**
- Package name: `theia-core`.
- Private package.
- CommonJS.
- Script: `start` runs `node server.js`.

**Library status:** `SUPPORT — THEIA GATEWAY / SERVER`

**Next action:**
- Fetch and document `server.js`.
- Decide whether this is canonical Theia runtime or superseded by monorepo `cores/theia-core`.

---

### 3.2 Theia inside `mirrornode/mirrornode`

**Role:** Monorepo workspace gateway.  
**Runtime:** TypeScript workspace.  
**Status:** Active/spec-support depending on build.

**Known code facts from monorepo README:**
- `cores/theia-core` is described as gateway.
- All MIRRORNODE traffic is supposed to flow through Theia.
- Smoke test: `npm run smoke:theia`.

**Library status:** `ACTIVE / NEED BUILD RECEIPT`

**Next action:**
- Run:
  ```bash
  npm run build:cores
  npm run smoke:theia
  ```

---

## 4. Catalyst OS / SHT Track

### 4.1 Catalyst OS archive / `mirrornode-with-catalyst-v0.2.0.tar.gz`

**Role:** SHT / tri-oracle harmonic verification mesh prototype.  
**Runtime:** Docker, TypeScript Express oracle services, React/Vite frontend.  
**Status:** Strong concept; needs local validation receipt.

**Known artifacts:**
- `catalyst_os/`
- `mirrornode-with-catalyst-v0.2.0.tar.gz`
- `services/oracle/index.ts`
- `services/oracle/Dockerfile`
- `docker-compose.yml`
- `setup.sh`
- `ui/src/components/RhythmHarmonicVisualizer.tsx`

**Known backend shape:**
- `POST /oracle`
- `GET /feedback`
- `GET /health`
- Ed25519 verification path using `ORACLE_PUBKEY` and `x-proof-signature`.
- NDJSON queue persistence: `./var/oracle-queue.ndjson`.
- Peer broadcast across Thoth, Hermes, Fox.

**Known frontend shape:**
- Oscillator/RK4 dynamics.
- Rhythm pattern and BPM.
- FFT / spectrum.
- Poincare section.
- Feedback-driven omega/alpha modulation.

**Library status:** `PROTOTYPE — NEED LOCAL RUN RECEIPT`

**Next action:**
```bash
tar -xzf mirrornode-with-catalyst-v0.2.0.tar.gz
cd mirrornode
chmod +x setup.sh
./setup.sh
curl http://localhost:7007/health
curl http://localhost:7007/feedback
docker compose logs -f thoth
```

---

## 5. Governance / Library / Documentation Repos

### 5.1 `mirrornode/mirrornode-index`

**Role:** Prior index/canon export surface.  
**Status:** Support / index.

**Known from prior work:**
- Was used for master/public/internal canon indexing.
- Potential place for cross-repo library exports.

**Library status:** `SUPPORT — INDEX / CANON EXPORT`

**Next action:**
- Compare with `mirrornode/library`.
- Avoid duplicating index repos unless one becomes archive.

---

### 5.2 `mirrornode/library`

**Role:** Dedicated library repo.  
**Status:** Empty or missing README in current check.

**Verified code facts:**
- Repository exists.
- `README.md` not found during this pass.

**Library status:** `TARGET — SHOULD RECEIVE THIS LIBRARY AFTER REVIEW`

**Next action:**
- Commit this document as `README.md` or `MIRRORNODE_PROJECT_CODE_LIBRARY.md`.
- Add subfolders:
  ```txt
  repos/
  concepts/
  routes/
  runbooks/
  evidence/
  ```

---

### 5.3 `mirrornode/mirrornode-docs`

**Role:** Documentation repo.  
**Status:** Support.

**Library status:** `SUPPORT — DOCS`

**Next action:**
- Use for polished docs; keep operational source-of-truth in `library` or `CORE-HUB`.

---

### 5.4 `mirrornode/MIRRORNODE-INFRA`

**Role:** Infrastructure/meta repo.  
**Status:** Placeholder/support.

**Library status:** `SUPPORT — INFRA PLACEHOLDER`

**Next action:**
- Only activate if it gains real Terraform/Vercel/DNS/GitHub Actions infra code.

---

## 6. Prototype / Archive / Experimental Repos

These repositories exist in the MIRRORNODE account and should be classified before active use.

| Repo | Likely role | Status |
|---|---|---|
| `mirrornode/INPphase` | Earlier INP/in-phase experiment | Prototype/archive |
| `mirrornode/rotan-resonance` | ROTAN resonance experiment | Prototype |
| `mirrornode/Fusion-Energy-Display-Web-Component---Grok_files` | Fusion display/Grok-export artifact | Archive/prototype |
| `mirrornode/biometric-integrated-meditative-RPG` | Biometric/meditative game concept | Prototype |
| `mirrornode/codespaces-react` | Codespaces React starter | Archive/dev scaffold |
| `mirrornode/Rotan-neural-modality-kids-game` | ROTAN kids game prototype | Prototype |
| `mirrornode/vite-react` | Generic Vite React starter | Archive/scaffold |
| `mirrornode/-mirrornode-core` | Older or misnamed core repo | Support/archive pending review |
| `mirrornode/Rotan-demo` | ROTAN demo | Prototype |
| `mirrornode/examples` | Examples repo | Support |
| `mirrornode/flags-sdk-hypertune-nextjs` | Hypertune/feature flags starter | Archive/prototype |
| `mirrornode/Trismcrownflowchart` | TRISM/crown flowchart artifact | Prototype/doc |
| `mirrornode/mirrornode-ring` | Ring/topology concept | Prototype/support |
| `mirrornode/MirrorNode-HUD-Engine-Interface-Governance-Specification` | HUD/specification repo | Support/doc |
| `mirrornode/Mirror_surface` | Mirror surface prototype | Prototype |
| `mirrornode/psp-audit` | Audit-related repo | Unknown/support |

**Next action for this entire group:**
- Do not develop from these until each receives one of:
  - `ACTIVE`
  - `SUPPORT`
  - `ARCHIVE`
  - `DELETE CANDIDATE`
- Add a one-line README/status file to each if it remains.

---

## 7. Current High-Value Development Tracks

### Track A — Health Stubs

**Surface:** `mirrornode-platform`  
**Status:** Ready concept; low-risk.  
**Files proposed:**
- `app/api/health/route.ts`
- `app/api/health/stripe/route.ts`
- `app/api/health/supabase/route.ts`
- `app/api/health/agents/route.ts`
- `app/api/health/ready/route.ts`

**Gate:**
- `/api/health` returns `200`.
- Component health routes return configured/unconfigured.
- `/api/health/ready` returns `200` only when all checks pass, otherwise `503 degraded`.

**Next action:** push as first PR.

---

### Track B — Stripe / Osiris Audit Commerce

**Surface:** `mirrornode-platform` only.  
**Status:** Architecture approved; code correction required.  
**Do not touch:** FastAPI `main.py`, verdict stream, `mirrornode-osiris`.

**Known required fixes:**
- Use `metadata`, not `meta`.
- Do not re-export scoped env bundles from `lib/env.ts` if that reintroduces top-level hard throws.
- Use `SUPABASE_SERVICE_ROLE_KEY`, not `SUPABASE_SERVICE_KEY`.
- Use Node runtime for Stripe routes.
- Use App Router raw body via `req.text()`.
- Remove Pages Router `bodyParser` config.
- For $149 Osiris Audit, prefer `mode: 'payment'`, not subscription, unless explicitly building recurring subscriptions.
- Avoid accepting arbitrary `priceId` from the client; use a server-owned price ID or allowlist.

**Next action:** corrected PR after Track A.

---

### Track C — Backend Contract / Dispatch Truth

**Surface:** `mirrornode-backend`.  
**Status:** Contract exists; implementation must be verified.

**Canonical claims to enforce:**
- `POST /dispatch` is real entry point.
- Truth surfaces: `/manifest`, `/lattice/status`, `/health`, `/heartbeat`, `/identity`.
- Non-real routes must not be documented as real.

**Next action:** run route/file audit.

---

### Track D — Canon Gate / Librarian / Judge

**Surface:** `MIRRORNODE-CORE-HUB`, `mirrornode-backend`, GitHub Actions.  
**Status:** Governance track; needs branch protection and CI receipts.

**Expected artifacts:**
- Canon Gate workflow.
- Frontmatter/claim class checks.
- Judge review rules.
- Librarian verification logic.
- Branch protection requiring checks.

**Next action:** collect workflow status, branch protection, and PR receipts.

---

### Track E — Catalyst OS / SHT

**Surface:** archive/local prototype.  
**Status:** Conceptually coherent; not yet promoted.

**Next action:** local validation and `SHT.md`.

---

## 8. Proposed Library Repo Structure

Use `mirrornode/library` as the dedicated index.

```txt
mirrornode/library/
├── README.md
├── MIRRORNODE_PROJECT_CODE_LIBRARY.md
├── repos/
│   ├── active.md
│   ├── support.md
│   ├── prototypes.md
│   └── archive.md
├── concepts/
│   ├── osiris-audit-commerce.md
│   ├── catalyst-os-sht.md
│   ├── canon-gate-librarian-judge.md
│   ├── hermes-test-harness.md
│   └── platform-health-stubs.md
├── routes/
│   ├── platform-routes.md
│   ├── backend-routes.md
│   └── osiris-routes.md
├── runbooks/
│   ├── local-validation.md
│   ├── vercel-deploy.md
│   ├── stripe-commerce.md
│   └── concept-reality-check.md
└── evidence/
    ├── github-repos-2026-05-29.md
    ├── env-guard-audit-2026-05-29.md
    └── catalyst-os-handoff-2026-05-29.md
```

---

## 9. Immediate Commands

### Platform

```bash
cd /Users/platform/code/mirrornode-platform
git status
npm run lint
npm run build
```

### Backend

```bash
cd /Users/platform/code/mirrornode-backend
git status
find . -maxdepth 3 -type f | sort
```

### Core Hub

```bash
cd /Users/platform/code/MIRRORNODE-CORE-HUB
git status
find canon protocols schemas state .github -maxdepth 3 -type f | sort
```

### Local Osiris

```bash
cd /Users/platform/code/mirrornode/mirrornode-osiris
git status
git remote -v
find . -maxdepth 3 -type f | sort
```

### Catalyst OS

```bash
tar -xzf mirrornode-with-catalyst-v0.2.0.tar.gz
cd mirrornode
chmod +x setup.sh
./setup.sh
curl http://localhost:7007/health
curl http://localhost:7007/feedback
```

---

## 10. Library Verdict

**Use this order:**

1. Stabilize `mirrornode-platform`.
2. Push Health Stubs.
3. Correct Stripe Commerce.
4. Verify backend contract routes.
5. Inventory `mirrornode-osiris`.
6. Validate Catalyst OS locally.
7. Promote this library into `mirrornode/library`.
8. Only then clean/merge/archive the prototype repos.

**Do not add new concepts until this library is committed and the first two platform PRs are closed.**

---

## Perplexity Session Log — 2026-05-29

### PRs opened in `mirrornode-platform`

- PR A #5 — `feat/health-stubs`
  - Status: open, not merged at time of logging.
  - Adds five health routes.
  - No env-module imports.
  - No Stripe, Supabase, agent SDK, FastAPI, or Osiris backend files.
  - Merge order: first.

- PR B #6 — `feat/stripe-commerce`
  - Status: open, not merged at time of logging.
  - Adds scoped env split plus Stripe checkout/webhook work.
  - Must be merged only after PR A.
  - Does not touch FastAPI, `main.py`, Osiris backend, or verdict stream.

### Confirmed architectural decisions

- Stripe/commercial payment work belongs in `mirrornode-platform`.
- FastAPI `main.py`, verdict stream, and Osiris backend work stay on the separate Osiris/backend track.
- `SUPABASE_SERVICE_KEY` naming is being corrected to `SUPABASE_SERVICE_ROLE_KEY`.
- Checkout Session metadata must use `metadata`, not `meta`.
- Stripe API version is pinned to `2025-03-31.basil` for this pass; do not casually upgrade during the same PR.
- `lib/env.ts` must not remain a global hard-throw detonation path for unrelated surfaces.

### Merge order

1. PR A #5 — health stubs.
2. PR B #6 — Stripe commerce/env split.
3. Osiris/FastAPI verdict stream only after commerce is deployed and verified.

---

## Shared State Sync — Simplified Process

Use this section as the internal process for cross-node handoffs. Keep it short.

### One-page sync shape

Each session or handoff should record only:

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

### Status words

Use only these status labels:

| Status | Meaning |
|---|---|
| `REAL` | Exists in code and has a receipt. |
| `PARTIAL` | Exists, but not fully wired or verified. |
| `SPEC` | Described but not implemented. |
| `BLOCKED` | A specific blocker prevents completion. |
| `ARCHIVE` | Keep for reference; do not actively build from it. |

### Receipt rule

No handoff is complete without one concrete receipt:

- PR link
- commit SHA
- file path
- passing CI run
- route response
- deployment URL
- terminal output
- audit artifact

### Boundary rule

Every sync must explicitly state what not to touch.

Example:

```txt
DO NOT TOUCH:
- FastAPI main.py
- Osiris verdict stream
- unrelated env keys
- prototype repos
```

### Default next-action rule

Only one next action should be assigned. If there are many, choose the one that unlocks the most reality with the least surface risk.
