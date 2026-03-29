# Deployment Checks

Pre-commit hooks for projects with a `backend/` (Python) and `frontend/` (JS/JSX) structure.

## What's Included

`basic-checks.yaml` contains hooks for:

**Backend (Python):**
- **Black** - Auto-formats code (line length: 120)
- **isort** - Sorts imports (Black-compatible)
- **Bandit** - Security scanning

**Frontend (JS/JSX):**
- **ESLint** - Linting via `npm run lint`
- **Prettier** - Format checking via `npm run format:check`
- **Build check** - Ensures the frontend builds without errors
- **No console.log** - Flags leftover `console.log` statements

**General:**
- Trailing whitespace and end-of-file fixes
- YAML/JSON validation
- Large file detection (>1MB)
- Merge conflict marker detection
- Hardcoded secrets scanning

## Setup

1. Install pre-commit:
   ```bash
   pip install pre-commit
   ```

2. Copy `basic-checks.yaml` to your repo root as `.pre-commit-config.yaml`:
   ```bash
   cp basic-checks.yaml /path/to/your/repo/.pre-commit-config.yaml
   ```

3. Install the hooks:
   ```bash
   pre-commit install
   ```

4. (Optional) Run against all files:
   ```bash
   pre-commit run --all-files
   ```

## Prerequisites

- Python 3 (for backend hooks)
- Node.js + npm (for frontend hooks)
- `frontend/package.json` must have `lint`, `format:check`, and `build` scripts
- `backend/pyproject.toml` must have a `[tool.bandit]` section

## Customization

- Adjust `files:` patterns if your directory structure differs
- Uncomment the flake8 hook for additional Python linting
- The TODO/FIXME checker runs only manually (`pre-commit run check-todos`) — remove `stages: [manual]` to run it on every commit
- Set `fail_fast: true` to stop on the first failure
