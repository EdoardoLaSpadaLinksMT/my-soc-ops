# Project Guidelines

## Mandatory Development Checklist

- Lint: `uv run ruff check .`
- Build/run: `uv run uvicorn app.main:app --reload --host 0.0.0.0 --port 8000`
- Test: `uv run pytest`

## Architecture

- This is a server-rendered FastAPI + Jinja2 + HTMX app, not a SPA; prefer template and HTMX fragment responses over new client-side state or JSON APIs unless required.
- Keep routes and template rendering in [app/main.py](../app/main.py), session state in [app/game_service.py](../app/game_service.py), bingo rules in [app/game_logic.py](../app/game_logic.py), and typed models in [app/models.py](../app/models.py).
- Use [app/templates/components](../app/templates/components) for HTMX-swapped fragments and [app/static](../app/static) for assets.

## Conventions

- Reuse the utility classes in [app/static/css/app.css](../app/static/css/app.css); follow [.github/instructions/css-utilities.instructions.md](instructions/css-utilities.instructions.md) for styling and [.github/instructions/frontend-design.instructions.md](instructions/frontend-design.instructions.md) for redesign work.
- Add route and rendered HTML tests in [tests/test_api.py](../tests/test_api.py) and deterministic rule tests in [tests/test_game_logic.py](../tests/test_game_logic.py).
- Sessions are in-memory by session cookie, so server restarts reset games; validate HTMX in a real browser, not the VS Code Simple Browser.
- Link to [README.md](../README.md) and [workshop/GUIDE.md](../workshop/GUIDE.md) instead of duplicating broader docs.
