# Branching Strategy

## Overview
This document outlines the Git branching strategy for the project.

## Branches

- `main`: Production-ready code. All releases are tagged from this branch.
- `develop`: Integration branch for features. Contains latest development changes.
- `feature/*`: Feature branches created from `develop`. Merge back into `develop` via PR.
- `hotfix/*`: Emergency fixes from `main`. Merge back into `main` and `develop`.
- `release/*`: Release preparation branches from `develop`. Merge into `main` and `develop`.

## Workflow

1. Start a new feature from `develop`: `git checkout -b feature/feature-name`
2. Commit changes and push feature branch
3. Open PR to `develop` for review
4. After PR approval and merge, delete feature branch
5. Periodically create release branches from `develop`
6. Hotfixes branch from `main` and merge bidirectionally

## Commit Messages

Use conventional commits format: `type(scope): description`

Types: feat, fix, docs, style, refactor, test, chore