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
