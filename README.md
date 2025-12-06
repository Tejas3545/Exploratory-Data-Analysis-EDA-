# Data Alchemy Lab

An intelligent, compact Streamlit app for exploratory data analysis (EDA) with optional AI-powered insights.
# Data Alchemy Lab

Comprehensive Exploratory Data Analysis (EDA) Streamlit application.

This repository provides a modular, production-oriented Streamlit app designed to help analysts and engineering teams explore, profile, clean, and visualize tabular datasets quickly and reproducibly. The project emphasizes clarity, maintainability, and practical deployment.

Table of contents
-----------------

- [Features](#features)
- [Quick start (local)](#quick-start-local)
- [Configuration](#configuration)
- [Project structure](#project-structure)
- [Testing](#testing)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

Features
--------

- Interactive data preview and column-level summaries
- Plotly-based visualizations integrated with Streamlit components
- Data cleaning utilities and outlier detection helpers
- Agent-driven automation primitives for repeatable workflows
- Optional AI-driven insights integration (e.g., Gemini) behind a feature flag

Quick start (local)
-------------------

Prerequisites

- Python 3.10 (recommended)
- Git

Create a virtual environment, install dependencies, and run the app:

```powershell
git clone https://github.com/Tejas3545/Exploratory-Data-Analysis-EDA-.git
cd Exploratory-Data-Analysis-EDA-
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
streamlit run app.py
```

On Unix/macOS:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
streamlit run app.py
```

Configuration
-------------

- Use a `.env` file in the repository root to provide any optional secrets or API keys. Example keys:

```
GOOGLE_API_KEY=your_api_key_here
```

Project structure and UI overview
---------------------------------

This section describes the intended repository layout and the UI design patterns used by the application. The goal is clarity for contributors while keeping runtime imports stable.

Top-level layout (highlighted files and folders):

- `app.py` — Streamlit entrypoint and router that composes the `ui` modules into pages
- `ui/` — UI components and page renderers. Each page is a small module exposing a `render_*` function (e.g. `render_overview`).
	- `ui/clean/` — cleaning utilities used by UI components (preview, apply, outlier detection)
- `data/` — small sample datasets (do not store production datasets here)
- `utils/` — helper functions and visualization wrappers that keep page code concise
- `eda.py` — business logic for EDA operations: descriptive statistics, transforms, and profiling
- `agents.py`, `memory.py` — optional automation/agents and session memory primitives
- `tests/` — unit tests and small fixtures
- `requirements.txt`, `constraints.txt` — pinned Python dependencies for reproducible installs
- `runtime.txt` — Streamlit Cloud Python runtime

UI Design conventions
---------------------

The app follows small, testable modules and consistent naming conventions:

- Page modules in `ui/` expose a single render entrypoint (e.g. `render_overview(df)`).
- Shared components (header, sidebar, CSS styles) are imported from `ui/header.py`, `ui/sidebar.py`, and `styles/`.
- Visualizations should be authored in `utils/sales_visualizations.py` or `ui/visuals.py` and return Plotly `fig` objects for the page to render with `st.plotly_chart(fig)`.
- Data transformations and heavy logic remain in `eda.py` or `utils/` (not in page modules) to keep UI fast and easy to test.

Suggested page layout (single-column main area with sidebar controls):

```
+-----------------------------------------------+
| HEADER (global)                               |
+-----------------------------------------------+
| SIDEBAR |                MAIN                 |
|        |  - Page title (h2)                   |
|        |  - Controls (filters, date pickers)  |
|        |  - Overview cards (small stats)      |
|        |  - Data preview table                |
|        |  - Visualizations (Plotly)           |
|        |  - Footer / attribution              |
+-----------------------------------------------+
```

Example: `Overview` page should present:

- A top row of compact KPI cards (rows, missing values, numeric columns, unique values)
- A data preview table (`st.dataframe`) with an action button to open a cleaner modal
- A responsive pair of charts (distribution and timeseries) below the table

Styling and themes
------------------

- Use `styles/` CSS files and `plotly_theme.py` to centralize visual tokens (colors, fonts).
- Keep dark/light theme toggles in the header for user preference.

Files safe to remove or exclude
------------------------------

- Local virtual environment folders (`.venv/`, `venv/`) — excluded by `.gitignore`.
- Binary caches / compiled artifacts (`__pycache__`, `.pyc`) — removed during cleanup.
- IDE config `.vscode/` if not used by the team.

If you want a follow-up step, I can:

- Produce a `UI style guide` markdown with component examples and code snippets
- Add a `docs/` folder with generated examples and screenshots
- Refactor a single page into the pattern above as an example PR


Testing
-------

Run unit tests with pytest:

```bash
pytest
```

Deployment
----------

Streamlit Cloud is supported (this repo includes `runtime.txt` and pinned constraints). For fully reproducible deployments, use a container-based workflow (Docker). Recommended steps for Streamlit Cloud:

1. Add repository to Streamlit Cloud.
2. Ensure the app uses Python 3.10 (the `runtime.txt` specifies `python-3.10.12`).
3. Clear build cache if you make changes to binary dependencies.

If you want a Docker setup, I can add a `Dockerfile` and `docker-compose.yml` that locks system packages and reproduces the environment exactly.

Housekeeping and repository hygiene
----------------------------------

- A `.gitignore` is included to exclude virtual environments, caches, and editor files.
- Generated bytecode caches (`__pycache__`) were removed in a cleanup commit.
- Keep large datasets out of the repository and provide sample data in `data/` or via a dataset download script under `utils/`.

Contributing
------------

Contributions are welcome. Suggested workflow:

1. Open an issue describing the change or problem.
2. Create a feature branch `feature/...` or bugfix branch `fix/...`.
3. Add tests for new behavior and ensure existing tests pass.
4. Submit a pull request with a clear description and linked issue.

License
-------

This repository does not include a license file yet. If you want an open-source license, I can add a recommended license (MIT or Apache-2.0) and a short contributor covenant if desired.

Next steps I can help with
-------------------------

- Generate a `Dockerfile` + `docker-compose.yml` for containerized deployment
- Add GitHub Actions to run tests and linters on PRs
- Add a docs site (mkdocs) for onboarding and API docs

Tell me which of the above you prefer and I will implement it.
