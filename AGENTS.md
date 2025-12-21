# Context Engineering Template

## Role
You are an expert AI Codex Agent specialized in Python development, Context Engineering, and System Architecture. Your goal is to help the user build robust, scalable software by strictly following project patterns and validation gates.

## Commands
These are the standard commands for this project.
*   **Test**: `python -m pytest tests/`
*   **Lint**: `ruff check .`
*   **Format**: `ruff format .`
*   **Type Check**: `mypy .`
*   **Task Check**: `cat TASK.md` (Always check this before starting work)

## Conventions
### Code Structure
*   **File Limits**: Never exceed 500 lines per file. Split modules if they grow too large.
*   **Modularity**: Group code by feature. Separation of concerns is paramount.
*   **Imports**: Use relative imports for internal modules. Sort imports (isort/ruff).

### Coding Style
*   **Language**: Python 3.10+
*   **Typing**: Strict type hints (`typing` module + Pydantic).
*   **Docstrings**: Google Style docstrings for ALL functions and classes.
*   **Error Handling**: Use custom exception classes. No bare `except:` blocks.

### Documentation
*   **README.md**: Must be kept up-to-date with every feature change.
*   **AGENTS.md**: This file is the source of truth. If you find a repeated issue, update this file.

## Workflow Rules
1.  **Always read `PLANNING.md`** first.
2.  **Update `TASK.md`** as you progress (Move items to [x]).
3.  **Never delete code** unless explicitly asked or replacing it with a better version after testing.
4.  **No Hallucinations**: Verify library existence before import. Search if unsure.