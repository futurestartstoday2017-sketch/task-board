# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project status

This is a new, currently empty project (`task-board`). There is no code, build system, or test suite yet. As the codebase grows, this file should be updated with:
- Build / lint / test commands (including how to run a single test)
- High-level architecture notes once there is a real structure to describe

## Git workflow rules

- **This project must always be a Git repository tracked on GitHub.** If a commit is about to be made and no Git repository exists yet, initialize one and set up the GitHub remote first.
- **Every time code is changed, commit the change and push it to GitHub.** Do not leave changes sitting locally uncommitted/unpushed — after any edit to source files, stage, commit with a clear message, and push to the remote (`origin`) immediately.
- Use descriptive commit messages that explain *why* the change was made, not just what changed.
- Do not force-push, rewrite history, or skip commit hooks unless explicitly instructed.
