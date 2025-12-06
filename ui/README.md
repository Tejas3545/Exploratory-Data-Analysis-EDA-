# UI components

This folder contains the UI modules used by the Exploratory Data Analysis app.

- `overview.py` — data preview and summary UI.
- `sales.py` — sales-related visualizations and controls.
- `visuals.py` — chart rendering utilities used by pages.
- `sidebar.py`, `header.py`, `profile.py`, `insights.py`, `css.py` — other UI pieces for the app layout and styling.
- `clean/` — helpers for dataset cleaning and preview actions.

Purpose:
- Make the `ui` folder self-documented for contributors.
- Provide quick navigation for future edits.

Notes:
- These are small, single-file modules; keeping them as modules (with `__init__.py`) makes imports explicit and test-friendly.
