# ⚽ Hot Tips

> A lightweight FastAPI service for exploring football fixtures and generating easy-to-read match predictions.

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-API-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![License](https://img.shields.io/badge/license-TBD-lightgrey)](#license)

## ✨ Overview

**Hot Tips** provides a simple JSON API for daily football predictions. It can retrieve fixtures from [API-Football](https://www.api-football.com/) when configured with an API key and falls back to sample fixtures for local development and demonstrations.

The project is designed as a clear starting point for building football-data applications, dashboards, notification bots, and prediction experiments.

## 🚀 Features

- **FastAPI-powered endpoints** with automatic interactive documentation.
- **Daily fixture lookup** across selected competitions.
- **API-Football integration** with a configurable API key.
- **Development fallback data** so the service can run without external credentials.
- **Simple prediction output** including:
  - estimated home-win probability,
  - suggested safe pick,
  - confidence label,
  - estimated expected goals,
  - first-10-minute no-goal indicator,
  - banker selections for an accumulator.
- **CORS middleware** for browser-based clients and prototypes.

> **Responsible use:** These predictions are illustrative estimates, not guarantees. Do not treat them as financial advice, and always comply with applicable laws and the terms of the data provider.

## 📡 API

### Health check

```http
GET /
```

Returns a basic service status and points to the predictions endpoint.

### Today's predictions

```http
GET /today
```

Returns the current date, generated predictions, and any selections classified as bankers.

### Interactive documentation

When the service is running, visit:

- [`/docs`](http://127.0.0.1:8000/docs) — Swagger UI
- [`/redoc`](http://127.0.0.1:8000/redoc) — ReDoc

## 🛠️ Getting started

### Prerequisites

- Python 3.10 or newer
- An optional API-Football account and API key for live fixtures

### Install

```bash
git clone https://github.com/aliabdiwali926-creator/Hot-tips.git
cd Hot-tips

python -m venv .venv
source .venv/bin/activate
# Windows PowerShell: .venv\Scripts\Activate.ps1

pip install fastapi uvicorn requests
```

### Configure live data

Set your API-Football key in the application configuration before requesting live fixtures:

```python
API_KEY = "YOUR_API_FOOTBALL_KEY"
```

For production use, prefer an environment variable or secret manager instead of committing credentials to source control.

### Run locally

Start the development server with:

```bash
uvicorn main:app --reload
```

Then open <http://127.0.0.1:8000/today> or explore the API through <http://127.0.0.1:8000/docs>.

> If the application file has a different name, replace `main:app` with `<module_name>:app`.

## 🧭 Example response shape

```json
{
  "date": "YYYY-MM-DD",
  "predictions": [
    {
      "league": "Premier League",
      "match": "Home FC vs Away FC",
      "time": "17:00",
      "xG": "1.6 - 1.1",
      "home_win_prob": "65%",
      "safe_pick": "1X Double Chance",
      "confidence": "75%",
      "no_goal_10min": "78%"
    }
  ],
  "SAFE_ACCA": []
}
```

## 🗺️ Roadmap

- [ ] Move API credentials to environment variables.
- [ ] Add a `requirements.txt` or `pyproject.toml` for reproducible installs.
- [ ] Add automated tests for prediction and fixture parsing.
- [ ] Use real team and league statistics instead of fixed xG estimates.
- [ ] Add structured error handling and API response validation.
- [ ] Add caching and rate-limit protection for external requests.
- [ ] Build a small web dashboard for browsing predictions.

## 🤝 Contributing

Contributions and ideas are welcome.

1. Fork the repository.
2. Create a branch: `git checkout -b feature/your-idea`
3. Make and test your changes.
4. Open a pull request with a clear description of the change.

## 📄 License

No license has been specified yet. Until a license is added, all rights remain with the repository owner and reuse should be considered restricted.

## 👤 Maintainer

Created and maintained by [aliabdiwali926-creator](https://github.com/aliabdiwali926-creator).

If you find the project useful, consider starring the repository ⭐
