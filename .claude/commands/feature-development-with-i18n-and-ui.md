---
name: feature-development-with-i18n-and-ui
description: Workflow command scaffold for feature-development-with-i18n-and-ui in hermes-webui.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /feature-development-with-i18n-and-ui

Use this workflow when working on **feature-development-with-i18n-and-ui** in `hermes-webui`.

## Goal

Implements a new feature that involves both backend (often Python API) and frontend (JS/HTML/CSS), with i18n keys added for all locales.

## Common Files

- `api/routes.py`
- `api/upload.py`
- `api/onboarding.py`
- `static/ui.js`
- `static/panels.js`
- `static/index.html`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Implement backend logic (api/*.py, e.g. routes.py, upload.py, onboarding.py).
- Update frontend JS for UI logic (static/ui.js, static/panels.js, etc).
- Update or create HTML elements as needed (static/index.html).
- Add or update CSS for styling (static/style.css).
- Add new i18n keys for all supported locales (static/i18n.js).

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.