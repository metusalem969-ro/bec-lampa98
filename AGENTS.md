# AGENTS.md

## Cursor Cloud specific instructions

### Product

**Lampa Bec** is a single-file static web demo (`index.html`): animated light bulb with **Aprinde** / **Stinge** buttons, status text (`Stins` / `Aprins`), and Space/Enter keyboard toggle. No backend, database, or package manager.

### Services

| Service | Required locally | Notes |
|---------|------------------|-------|
| Static HTTP server | Yes (dev only) | Serves `/workspace`; production is GitHub/GitLab Pages (see `README.md`) |

### Running locally

From the repo root:

```bash
python3 -m http.server 8080
```

Open http://127.0.0.1:8080/ (or `http://localhost:8080/`).

Use a tmux session for long-running dev servers so the process survives backgrounding (see Cloud Agent shell guidance).

### Lint / test / build

This repo has **no** `package.json`, Makefile, or test runner. There is nothing to lint or unit-test in CI beyond manual/browser checks. GitLab CI (`.gitlab-ci.yml`) only copies static files into `public/` for Pages deploy.

### Hello-world verification

1. Load the app in a browser.
2. Click **Aprinde** → status **Aprins**, bulb glows, background brightens.
3. Click **Stinge** → status **Stins**, bulb off.
4. Press **Space** to toggle on/off again.

### Deploy

- **GitLab Pages**: push to `main`; CI `pages` job publishes `index.html` and `.nojekyll`.
- **GitHub Pages**: configured in repo settings; canonical URL in `index.html` and `README.md`.
