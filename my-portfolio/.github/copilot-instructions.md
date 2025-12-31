# Copilot / AI Agent Instructions

Purpose: Help AI coding agents become productive quickly in this repository by describing the project's structure, key workflows, conventions, and where to look for examples.

1. Quick repo state
- This repository currently has no source files at the root; agents should run a quick file listing to discover the project layout (e.g. `ls -la`).

2. First steps for the agent
- Run a file search for common entry points: `package.json`, `pyproject.toml`, `src/`, `README.md`, `Makefile`, `.github/workflows/`.
- If a `README.md` exists, prefer it for high-level architecture and run/build commands.

3. Architecture discovery checklist
- Look for a top-level `src/` (or `app/`, `lib/`) directory to identify main components.
- Check `package.json` / `pyproject.toml` for scripts: use `npm run` / `poetry run` commands for build/test.
- Inspect `.github/workflows/` for CI steps that reveal test and lint commands.

4. Common patterns to surface (if present)
- Frontend frameworks: look for `vite.config.js`, `next.config.js`, `angular.json` to identify framework-specific flows.
- Backend services: scan for `server.js`, `app.py`, `main.go` to find service entrypoints and env expectations.
- Monorepos: detect `packages/` or `workspaces` in `package.json`.

5. Build / Test / Debug heuristics
- Prioritize project-provided scripts over guessing commands. Example checks:
  - `package.json` -> `scripts.test`, `scripts.build`
  - `pyproject.toml` -> `[tool.pytest]` sections or `scripts` table
  - `.github/workflows/*` -> look for `run:` steps with test commands
- If none present, propose minimal commands (ask before running): `npm test`, `pytest`, `go test`.

6. Conventions & patterns to follow when editing
- Keep changes minimal and focused: prefer small commits that fix the root cause.
- Preserve existing code style; follow the repository's existing import/formatting patterns.
- When adding new files, update `README.md` or top-level documentation with run steps.

7. Integration & external dependencies
- Inspect `package.json`, `requirements.txt`, `pyproject.toml`, `go.mod` to list external deps and typical install commands.
- Search for `DATABASE_URL`, `REDIS_URL`, or `GCP_`, `AWS_` env var usage to identify infra integrations.

8. When the repo is empty or missing CI/docs
- Create small, clearly signposted PRs: add `README.md` with run steps, add `package.json`/`pyproject.toml` if scaffolded, or ask the human for preferred stack choices.

9. Examples & placeholders for common edits
- If adding a README entry for `npm` projects, include:
  - `npm install`
  - `npm run build`
  - `npm test`
- If adding Python instructions, include `python -m venv .venv`, `pip install -r requirements.txt`, `pytest`.

10. Interaction & safety
- Do not commit secrets. If secrets are required, add a `README` placeholder explaining required env vars but not values.
- If uncertain about a structural decision, add a short TODO comment and open a draft PR asking the maintainer.

If you'd like, I can (1) tailor this file with discovered examples once you add project files, or (2) open a draft PR now. What would you prefer?