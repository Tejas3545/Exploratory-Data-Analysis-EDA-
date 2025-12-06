# Data Alchemy Lab

An intelligent, compact Streamlit app for exploratory data analysis (EDA) with optional AI-powered insights.
# Data Alchemy Lab

Professional Exploratory Data Analysis (EDA) Streamlit application.

This repository contains a lightweight, production-minded Streamlit app that helps analysts and product teams quickly explore, profile, clean, and visualize tabular datasets. It includes opinionated defaults for usability, a modular UI, and optional AI-driven insights.

## Features
- Interactive data preview, filtering and summary statistics
- Visualizations powered by Plotly and Streamlit components
- Data cleaning utilities and outlier detection
- Agent-based automation hooks for repeatable workflows
- Optional AI integration (Gemini/LLM) for natural-language insights

## Quick Start (Local development)
Prerequisites:
- Python 3.10 (recommended)
- Git

Clone and run locally:

```powershell
git clone https://github.com/Tejas3545/Exploratory-Data-Analysis-EDA-.git
cd Exploratory-Data-Analysis-EDA-
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
streamlit run app.py
```

On Unix/macOS use `source .venv/bin/activate` to activate the virtualenv.

Environment variables
- Create a `.env` file in the repository root to provide optional keys used by the app (e.g. `GOOGLE_API_KEY` for Gemini integration).

## Deployment

Recommended: Streamlit Cloud or any container platform. This repo contains a `runtime.txt` and pinned constraints to keep builds reproducible on Streamlit Cloud. For full control, use the included Docker instructions below.

### Streamlit Cloud
- Add the repository to Streamlit Cloud and point it at `app.py`.
- Ensure the app uses Python 3.10 (the `runtime.txt` sets `python-3.10.12`).
- Clear build cache if you change binary dependencies.

### Docker (optional)
If you prefer a containerized deployment, a `Dockerfile` can be added to pin system-level dependencies and reproduce the same environment everywhere. Ask the maintainer to generate one and I'll include it.

## Project layout

- `app.py` — Streamlit entrypoint and app orchestration
- `ui/` — UI modules (header, sidebar, pages, CSS)
- `ui/clean/` — dataset cleaning helpers
- `data/` — sample or generated datasets
- `utils/` — utility functions and visualization helpers
- `eda.py` — EDA helpers: profiling, outliers, and transformations
- `agents.py`, `memory.py` — optional agent-driven automation
- `requirements.txt`, `constraints.txt` — pinned Python dependencies
- `runtime.txt` — Streamlit Cloud Python runtime

## Tests

Unit tests are located in `tests/`. Run them with `pytest`:

```bash
pytest
```

## Contributing

Contributions are welcome. Please open an issue to discuss larger changes before submitting a PR. Keep changes small and self-contained. Use the existing code style and write tests for new functionality.

## Housekeeping
- This repository now includes a `.gitignore` to exclude editor and build artifacts. Temporary caches (`__pycache__`, `.pyc`) were removed in a cleanup commit.

## License
Add a LICENSE file to indicate the project's license. If you want, I can add an open-source license (MIT/Apache-2.0) for you.

---

If you'd like, I can also:

- Generate a `Dockerfile` and `docker-compose.yml` for containerized deployment
- Add GitHub Actions for linting, tests, and CI
- Produce a docs site (mkdocs) for developer onboarding

Tell me which of these you'd like next and I'll implement it.