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
