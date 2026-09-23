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

## 技術スタック

- **フレームワーク**: React 19
- **ビルドツール**: Vite 8(`@vitejs/plugin-react`)
- **言語**: JavaScript(JSX)。TypeScriptは未導入。
- **スタイリング**: プレーンCSS(`App.css` / `index.css`)。CSSフレームワークやCSS-in-JSは未使用。
- **状態管理**: Reactの`useState`のみ。外部の状態管理ライブラリは未導入。
- **永続化**: ブラウザの`localStorage`(キー: `task-board.tasks`)。バックエンド・DBは無し。
- **Lint**: oxlint(`npm run lint`)。テストフレームワークは未導入。
- **パッケージマネージャ**: npm

## コンポーネントの命名規約

現状コンポーネントは`src/App.jsx`の1つのみだが、今後追加する場合は以下の規約に従う。

- コンポーネントファイルは**PascalCase**(例: `App.jsx`)とし、ファイル名はデフォルトエクスポートするコンポーネント名と一致させる。
- コンポーネント専用のスタイルは、同名の`.css`ファイルとして同じディレクトリに配置する(例: `App.jsx` ↔ `App.css`)。
- 複数コンポーネントに分割する場合は`src/components/`配下に置き、1ファイル1コンポーネントとする。

## デプロイ先

https://futurestartstoday2017-sketch.github.io/task-board/

GitHub Pagesにデプロイされており、`.github/workflows/deploy.yml`が`main`へのpushのたびにビルド・公開する(`actions/upload-pages-artifact` + `actions/deploy-pages`)。`vite.config.js`は`base: '/task-board/'`を設定しており、Pagesのプロジェクトサイトのパスと一致させている——リポジトリ名を変更する場合はここも合わせて変更すること。

リポジトリのPages設定(Settings → Pages)で、SourceをGitHub Actionsにしておく必要がある。

## Git workflow rules

- **This project must always be a Git repository tracked on GitHub.** If a commit is about to be made and no Git repository exists yet, initialize one and set up the GitHub remote first.
- **Every time code is changed, commit the change and push it to GitHub.** Do not leave changes sitting locally uncommitted/unpushed — after any edit to source files, stage, commit with a clear message, and push to the remote (`origin`) immediately.
- Use descriptive commit messages that explain *why* the change was made, not just what changed.
- Do not force-push, rewrite history, or skip commit hooks unless explicitly instructed.
