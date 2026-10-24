# Britume — early web MVP

**Original social/community concept:** connect with people, discover communities, and keep media you have permission to use.

This is a responsive, installable web prototype intended as the first repository milestone. It is deliberately honest about its current limitations: it is **not yet a production social network** and it has no remote database, authentication, shared feed, moderation service, licensed music catalog, or real-time communications backend.

## What works in this preview

- Responsive desktop and mobile navigation
- Sample feed, discover page, sample profiles, and community cards
- Create local text/photo posts; choose a local visibility label
- Like local posts, delete local posts, and browse sample content
- Edit a local profile and save preferences in browser storage
- Follow sample profiles and join sample circles locally
- Select personal audio files and list them in a local preview library
- PWA manifest and service worker for caching the app shell

## What is not implemented yet

- Secure sign-up/login, account recovery, or cross-device profiles
- Shared cloud posts, comments, follow relationships, or communities
- Enforced public/private access control; current privacy controls are UI-only
- Actual audio upload, durable offline audio playback, video downloads, or media licensing
- Expiring shared stories, voice messaging, calls, live streaming, push notifications
- Reporting, blocking, moderation queues, rate limiting, production analytics

Do not collect real users' sensitive data or announce this preview as a secure production social network until these controls exist.

## Run locally

This is a static site and needs no build step. Serve this directory over HTTP, for example:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`.

## Publish on GitHub Pages

1. Create a repository named `britume` in your own GitHub account.
2. Upload all files in this folder, keeping the `assets/` directory.
3. Open **Settings → Pages** in the repository.
4. Select **Deploy from a branch**, choose `main` and `/ (root)`, then save.
5. Wait for the Pages deployment to finish and test the resulting site on desktop and Android.

For a project site at `https://OWNER.github.io/britume/`, this app uses relative paths. The service worker and manifest are scoped to the project directory.

## Suggested production architecture

- Frontend: React + Vite or a carefully maintained component-based web app
- Backend: authenticated API + PostgreSQL database + object storage
- Media: upload validation, file-size/type limits, rights metadata, signed URLs, and deletion lifecycle
- Security: server-side authorization, secure sessions, privacy enforcement, rate limits, abuse reports, blocking, audit logs
- Realtime: separately scoped messaging/call/live-stream infrastructure
- Android: Capacitor wrapper or a native client after the web experience and backend contracts are stable

## Launch gate

Before public production release, implement and test authentication, server-enforced privacy, reporting/blocking, media upload security, deletion/retention policies, terms, privacy notice, and a moderation response process. Confirm music and video licensing before distributing other people's content.
