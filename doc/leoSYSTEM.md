# Leopold Nature Observer — Compiled System Reference

**Designation:** leo
**Document role:** Canonical compiled technical reference for Leopold Nature Observer
**Source:** `doc/system/`
**Build command:** `bash doc/system/BUILD.sh`
**Document version:** 1.0 (2026-09-24) — initial doc/system authored from scratch
**Protocol:** BDS Documentation Protocol v2.0

> **Generated artifact warning:** `doc/leoSYSTEM.md` is assembled output.
> Edit the source modules under `doc/system/` and rebuild. Hand edits to
> generated artifacts are overwritten by the next build.

This `doc/system/` tree is the canonical source of truth for Leopold Nature
Observer. It uses explicit **truth classes**: canonical facts define role
and what actually exists in this checkout versus what's referenced but not
found; snapshot facts are dated, audit-derived observations. This tree
records an unresolved structural question (the root vs. `leopold-frontend/`
dual `package.json` layout) rather than silently picking an answer — see
`01-overview-philosophy.md`.

Assembly contract:

- Command: `bash doc/system/BUILD.sh`
- Validation: `bash doc/system/validate_snapshots.sh` runs during assembly
- Primary output: `doc/leoSYSTEM.md`

| Part | File | Contents |
| --- | --- | --- |
| §1 | `01-overview-philosophy.md` | Purpose, and the frontend-only / dual-package.json open questions |
| §2 | `02-architecture.md` | PWA architecture: audio, maps, offline |
| §3 | `03-tech-stack.md` | Stack details |
| §4 | `04-project-structure.md` | Directory layout |
| §5 | `05-config-env.md` | Environment variables (backend location undetermined) |
| §6 | `90-handover.md` | Open structural question, testing, chapter-authoring caveats |

## Quick Assembly

```bash
bash doc/system/BUILD.sh
```

---

# Overview and Philosophy

Leopold Nature Observer is a SvelteKit application for wildlife observation
and community science: recording observations via photo and audio, with
interactive maps and (per the README) AI-assisted species identification.

**Canonical fact — this checkout is frontend-only.** No backend code exists
in this repository. `README.md` (in `leopold-frontend/`) documents
`VITE_API_URL` and `VITE_WS_URL` environment variables, implying a backend
API this repo depends on — but no `.env.example` file exists in the
repository to confirm this directly, and that backend's location is not
established anywhere in this repo. Do not assume a backend exists elsewhere
in this workspace without confirming it directly; none was found while
authoring this chapter.

**Canonical fact — two `package.json` files, unresolved relationship:**
this repository has a `package.json`/`bun.lock`/build config at its root
(scripts: `vite dev`, `vite build`, etc.) **and** a second, complete
SvelteKit application under `leopold-frontend/` with its own
`package.json`, `src/`, and config. The root has no `src/` directory of its
own, so its `vite dev`/`vite build` scripts would have nothing to build
from that location. `CONVERSION_SUMMARY.md` (a repo-root status file)
mentions updating "both `package.json` files," implying this dual structure
was deliberate at some point — but this chapter does not establish whether
the root-level config is a currently-used wrapper, a stale leftover from
before code moved into `leopold-frontend/`, or something else. Treat
`leopold-frontend/` as where the real application code lives until this is
resolved.

---

# Architecture

**Canonical fact:** the application (under `leopold-frontend/`) is a
SvelteKit Progressive Web App with client-side audio processing and map
integration; it holds no server-side logic of its own beyond what SvelteKit
provides.

**Canonical fact — audio:** real-time audio recording and processing use
the Web Audio API directly in the browser (waveform visualization,
spectrogram generation, feature extraction for species identification),
per `leopold-frontend/README.md`. Multiple format support (WebM, MP4, WAV)
is described there; this was not independently re-verified against the
component code while authoring this chapter.

**Canonical fact — maps:** interactive maps use Leaflet with marker
clustering, per the same README.

**Canonical fact — offline:** the app is a full PWA (service worker,
offline observation recording, background sync), per the same README.

**Not yet established here:** where AI species identification (mentioned
in both this repo's root README and `leopold-frontend/README.md`) is
actually implemented — no model or inference code was located while
authoring this chapter. It may depend on the undetermined backend
referenced in `01-overview-philosophy.md`.

---

# Tech Stack

**Canonical fact:**

- SvelteKit
- TypeScript
- Tailwind CSS
- Leaflet (maps)
- Web Audio API (browser-native, no separate audio library dependency
  confirmed)
- Bun (per `CONVERSION_SUMMARY.md`, the project was converted from
  npm/yarn to Bun on 2025-10-18; `bun.lock` files exist at both the repo
  root and in `leopold-frontend/`)

**Not yet established here:** the exact npm/Bun dependency list was not
enumerated chapter-by-chapter from `leopold-frontend/package.json` — read
that file directly for the authoritative, current list.

---

# Project Structure

```text
leopold-frontend/        The actual SvelteKit application (see 01-overview-philosophy.md)
  src/
    lib/
      components/         AudioRecorder.svelte, ObservationMap.svelte,
                           ObservationForm.svelte, and others
      stores/              Svelte stores for state management
      types/               TypeScript type definitions
      utils/               Utility functions
      api/                 API client and services
    routes/
      +layout.svelte       Main application layout
      +page.svelte         Home page (map view)
      auth/                Authentication pages
      observations/        Observation-related pages
    app.html, app.css
    service-worker.js       PWA service worker
  package.json, bun.lock, svelte.config.js, tailwind.config.js

(repo root)
  package.json, bun.lock   Second, root-level config with no src/ of its own
                           — see 01-overview-philosophy.md
  *.md                     Numerous status/summary files (dark-mode guides,
                            conversion summary, feature-implementation
                            reports, lint reports) — treat each as a dated
                            point-in-time record, not current architecture
```

---

# Configuration and Environment

**Canonical fact:** `leopold-frontend/README.md` documents these
environment variables (no `.env.example` file exists in the repository to
confirm them directly — verify in `leopold-frontend/src/` before relying on
exact names):

- `VITE_API_URL` — backend API base URL (backend location undetermined,
  see `01-overview-philosophy.md`)
- `VITE_WS_URL` — WebSocket URL
- `VITE_ENABLE_AUDIO_FEATURES` — feature flag
- `VITE_ENABLE_OFFLINE_MODE` — feature flag

**Canonical fact:** production deployment requires HTTPS specifically for
microphone access (`getUserMedia`), per the same README.

---

# Handover

**Canonical fact — biggest open question:** the root-vs-`leopold-frontend/`
dual-`package.json` structure (see `01-overview-philosophy.md`) should be
resolved before anyone builds new tooling against this repo's root. Whoever
picks this up should determine whether the root config is dead weight
(safe to remove) or serves a real purpose (e.g. a monorepo wrapper, a
GitHub Pages deploy step — the root `package.json`'s own `deploy` script
targets `gh-pages`), and document the answer here.

**Canonical fact:** this repo carries a large number of top-level status
files (`FINAL_STATUS.md`, `PROJECT_STATUS.md`, `IMPLEMENTATION_COMPLETE.md`,
`FEATURES_IMPLEMENTED.md`, dark-mode guides, `ERROR_REPORT.md`,
`LINT_ERRORS_DETAILED.md`). This `doc/system/` tree does not attempt to
reconcile or summarize them — treat each as a dated snapshot, not current
truth.

**Canonical fact — testing:** `cd leopold-frontend && bun test` (or `npm
test`), running Vitest. `bun run test:watch` for watch mode.

**Known limitation of this chapter set:** authored from `README.md` (repo
root), `leopold-frontend/README.md`, `CONVERSION_SUMMARY.md`, and a direct
directory listing — not from running the application, reading component
source in depth, or locating the backend/AI-identification service this
frontend expects to talk to.
