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
