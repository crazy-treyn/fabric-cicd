# AGENTS.md

## Cursor Cloud specific instructions

This is a **Python library** (not a web app or service). There is no server to start. All testing is done via `pytest` with mocked API calls — no Azure credentials or external services are needed for development.

### Quick reference

| Task | Command |
|---|---|
| Install/sync deps | `uv sync --python 3.11` |
| Run tests | `uv run pytest` |
| Lint check | `uv run ruff check` |
| Format check | `uv run ruff format --check` |
| Auto-format | `uv run ruff format` |
| Build docs | `uv run mkdocs serve` |

### Key caveats

- Python 3.11 is pinned in `.python-version`; use `uv sync --python 3.11` (uv manages the Python install).
- `uv` is the sole package manager; do not use `pip` directly.
- The library calls Microsoft Fabric REST APIs at runtime, but **all tests are unit tests with mocked HTTP** — no Azure/Fabric credentials needed.
- `ruff format --check` may report one pre-existing formatting diff in `src/fabric_cicd/fabric_workspace.py`; this is a known upstream issue, not caused by agent changes.
- `ruff check` should pass clean on `main`.
- The project uses `setuptools` as its build backend with dynamic versioning from `fabric_cicd.constants.VERSION`.
- See `CONTRIBUTING.md` for full contributor workflow (changie, PR conventions, etc.).
