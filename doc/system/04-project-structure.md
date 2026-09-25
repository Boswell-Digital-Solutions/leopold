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
