# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

A React task board app (Vite + React 19). Single-page app with no backend — task state lives in `App.jsx` (`useState`) and is persisted to the browser's `localStorage` (key `task-board.tasks`) so it survives page reloads.

## Commands

- `npm install` — install dependencies
- `npm run dev` — start the Vite dev server
- `npm run build` — production build (outputs to `dist/`)
- `npm run preview` — preview the production build locally
- `npm run lint` — run oxlint

There is no test suite configured yet.

## Architecture

- `src/main.jsx` — entry point, mounts `App` into `#root`.
- `src/App.jsx` — contains all task board logic and UI: task list state, add/toggle/delete handlers, and rendering. There is currently no separate component split or state management library — everything lives in this single component.
- `src/App.css` — styles for the task board (form, list, completed-task graying).
- `src/index.css` — global page styles.

## Deployment

Deployed to GitHub Pages at `https://futurestartstoday2017-sketch.github.io/task-board/`, built by `.github/workflows/deploy.yml` on every push to `main` (via `actions/upload-pages-artifact` + `actions/deploy-pages`). `vite.config.js` sets `base: '/task-board/'` to match the Pages project-site path — keep this in sync if the repo is ever renamed.

The repository's Pages source must be set to "GitHub Actions" (Settings → Pages) for the workflow's deploys to take effect.

## Git workflow rules

- **This project must always be a Git repository tracked on GitHub.** If a commit is about to be made and no Git repository exists yet, initialize one and set up the GitHub remote first.
- **Every time code is changed, commit the change and push it to GitHub.** Do not leave changes sitting locally uncommitted/unpushed — after any edit to source files, stage, commit with a clear message, and push to the remote (`origin`) immediately.
- Use descriptive commit messages that explain *why* the change was made, not just what changed.
- Do not force-push, rewrite history, or skip commit hooks unless explicitly instructed.
