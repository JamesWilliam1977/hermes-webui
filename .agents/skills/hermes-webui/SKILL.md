```markdown
# hermes-webui Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute effectively to the `hermes-webui` codebase, a Python-based web application with a custom frontend (JS/HTML/CSS) and backend (Python, no major framework detected). You'll learn the project's coding conventions, common workflows for adding features, fixing bugs, updating models/providers, UI refactoring, and infrastructure changes, as well as how to write and organize tests.

## Coding Conventions

- **File Naming:**  
  Use `snake_case` for Python files and directories.  
  *Example:*  
  ```
  api/routes.py
  api/onboarding.py
  ```

- **Import Style:**  
  Use relative imports within Python modules.  
  *Example:*  
  ```python
  from .providers import ProviderList
  ```

- **Export Style:**  
  Use named exports for both Python and JS modules.  
  *Example (Python):*  
  ```python
  def get_user():
      ...
  ```
  *Example (JS):*  
  ```js
  export function updateUI() { ... }
  ```

- **Commit Messages:**  
  - Use prefixes: `fix`, `feat`, `chore`
  - Keep messages concise (~54 characters on average)
  - *Example:*  
    ```
    fix: handle missing provider in onboarding flow
    feat: add support for new language in i18n
    chore: update dependencies
    ```

## Workflows

### Feature Development with i18n and UI
**Trigger:** When adding a new user-facing feature involving backend, frontend, and internationalization  
**Command:** `/new-feature-i18n-ui`

1. Implement backend logic in `api/*.py` (e.g., `routes.py`, `upload.py`, `onboarding.py`).
2. Update frontend JS for UI logic (`static/ui.js`, `static/panels.js`, etc).
3. Update or create HTML elements as needed (`static/index.html`).
4. Add or update CSS for styling (`static/style.css`).
5. Add new i18n keys for all supported locales (`static/i18n.js`).
6. Write or update tests if applicable (`tests/...`).

*Example (i18n key addition in JS):*
```js
i18n['en']['welcome_message'] = "Welcome!";
i18n['es']['welcome_message'] = "¡Bienvenido!";
```

---

### Model or Provider Addition or Update
**Trigger:** When adding or updating a model/provider (backend config, frontend dropdowns, onboarding)  
**Command:** `/add-model-provider`

1. Update model/provider lists and mappings in backend config (`api/config.py`, `api/providers.py`).
2. Update frontend dropdowns or UI mappings (`static/index.html`, `static/ui.js`).
3. Update onboarding/setup flows if needed (`api/onboarding.py`, `api/routes.py`).
4. Update or add tests to verify new models/providers appear (`tests/...`).

*Example (Python config):*
```python
MODELS = {
    "gpt-4": {...},
    "hermes-new-model": {...}
}
```

---

### Bugfix with Targeted Test
**Trigger:** When fixing a bug and ensuring it doesn't recur  
**Command:** `/bugfix-with-test`

1. Identify and fix the bug in the relevant source file(s) (`api/*.py`, `static/*.js`).
2. Add or update a test covering the bug scenario (`tests/test_issueXXX_*.py` or similar).

*Example (test file):*
```python
def test_issue123_upload_limit():
    # Test for upload limit bug
    ...
```

---

### UI Component Refactor or Removal
**Trigger:** When refactoring, replacing, or removing a UI element  
**Command:** `/ui-refactor`

1. Remove or refactor the JS logic for the component (`static/*.js`).
2. Remove or update the HTML markup (`static/index.html`).
3. Remove or update CSS rules (`static/style.css`).
4. Update i18n keys if tooltips/labels change (`static/i18n.js`).
5. Update or remove related tests (`tests/...`).

*Example (removing a button in HTML):*
```html
<!-- Remove this block -->
<!-- <button id="old-feature-btn">Old Feature</button> -->
```

---

### Test-Driven Infrastructure Change
**Trigger:** When making backend/infrastructure changes and ensuring correctness with tests  
**Command:** `/infra-change-with-test`

1. Implement backend change (`api/*.py`).
2. Add a new test file or update an existing one to cover the new logic (`tests/test_*.py`).

*Example (Python test):*
```python
def test_new_infra_behavior():
    # Assert new backend behavior
    ...
```

## Testing Patterns

- **Framework:** Unknown (likely custom or standard Python testing)
- **Test File Naming:**  
  - Python: `tests/test_*.py`, `tests/test_issue*.py`
  - JS/TS: `*.test.ts` (for frontend logic)
- **Test Location:**  
  - All tests are under the `tests/` directory
- **Test Coverage:**  
  - Add or update tests for every new feature, bugfix, or infrastructure change
- **Example (Python):**
  ```python
  def test_feature_enabled():
      assert feature.is_enabled() is True
  ```

## Commands

| Command                | Purpose                                                          |
|------------------------|------------------------------------------------------------------|
| /new-feature-i18n-ui   | Start a new feature involving backend, UI, and i18n              |
| /add-model-provider    | Add or update a model/provider (backend & frontend)              |
| /bugfix-with-test      | Fix a bug and add a targeted regression test                     |
| /ui-refactor           | Refactor or remove a UI component and update related assets      |
| /infra-change-with-test| Make infrastructure/backend changes with dedicated tests          |
```
