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
