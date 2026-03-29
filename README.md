# Deployment Checks

Ready-to-use [pre-commit](https://pre-commit.com/) hook configurations for Python and JavaScript projects.

## Files

| File | Stack | Hooks |
|------|-------|-------|
| `python-checks.yaml` | Python | Black, isort, Bandit, secrets scanner |
| `js-checks.yaml` | JS/TS (React, Node) | ESLint, Prettier, build check, no console.log, secrets scanner |

Both files also include general checks: trailing whitespace, end-of-file fixer, YAML/JSON validation, large file detection, and merge conflict markers.

## Setup

1. Install pre-commit:
   ```bash
   pip install pre-commit
   ```

2. Copy the relevant file to your repo root as `.pre-commit-config.yaml`:
   ```bash
   # For Python projects
   cp python-checks.yaml /path/to/your/repo/.pre-commit-config.yaml

   # For JS/TS projects
   cp js-checks.yaml /path/to/your/repo/.pre-commit-config.yaml
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

**Python (`python-checks.yaml`):**
- Python 3

**JavaScript (`js-checks.yaml`):**
- Node.js + npm
- `package.json` must have `lint`, `format:check`, and `build` scripts

## Customization

- Uncomment the flake8 hook in `python-checks.yaml` for additional Python linting
- The TODO/FIXME checker runs only manually (`pre-commit run check-todos`) — remove `stages: [manual]` to run it on every commit
- Set `fail_fast: true` to stop on the first failure
- Adjust file patterns to match your project structure

## License

[MIT](LICENSE)
