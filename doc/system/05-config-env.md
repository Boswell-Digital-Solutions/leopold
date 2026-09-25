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
