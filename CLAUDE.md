# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

**Run the app:**
```bash
python src/app.py
# Visit http://127.0.0.1:5000
```

**Install dependencies:**
```bash
uv pip install -r requirements.txt
```

**Run all tests:**
```bash
python -m unittest discover -s tests
```

**Run a single test:**
```bash
python -m unittest tests.test_app.AppTestCase.test_index
```

## Architecture

This is a minimal Flask web app structured as a starter template for a course-explainer feature.

- [src/app.py](src/app.py) — Flask entry point. Registers two URL rules: `/` → `index` and `/course/<course_id>` → `course`. Imports view functions directly from `views` (no blueprint).
- [src/views.py](src/views.py) — View functions. Currently stubs that render templates; course data is not yet wired from `models.py` into `course.html`.
- [src/models.py](src/models.py) — Defines a `Course` dataclass and a hardcoded `courses` list (3 entries). This list is the intended data source for views but is not yet imported or used in `views.py`.
- [src/templates/](src/templates/) — Jinja2 templates. `layout.html` is included (not extended) via `{% include %}` inside `index.html` and `course.html`.

**Key gap in the starter template:** `models.py` defines course data but `views.py` does not import or pass it to templates — connecting these is the primary task this template is designed to scaffold.

The test suite in [tests/test_app.py](tests/test_app.py) adds `src/` to `sys.path` manually so imports work without package installation.

## Add Unit tests
- Whenever you add any new changes, add unit tests and run and make sure the tests passes.