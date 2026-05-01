# MetroPT-3 Predictive Maintenance Dashboard

A Streamlit dashboard with a Flask inference API for industrial equipment failure prediction.

## Repository contents

- `streamlit_app.py` — Streamlit dashboard UI
- `model_api.py` — Flask API for prediction and feature importance
- `saved_models/` — model artifacts required at runtime
- `download_models.sh` — optional helper to fetch model files from environment-defined URLs
- `notebook/` — dataset and model exploration notebooks

## Requirements

- Python 3.9+
- `pip install -r requirements.txt`

## Setup

1. Create and activate a virtual environment:

```bash
python -m venv .venv
# Windows
.\.venv\Scripts\activate
# macOS / Linux
source .venv/bin/activate
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Ensure the `saved_models/` directory contains the required artifacts:

- `features.pkl`
- `rf_model.pkl`
- `rf_threshold.pkl`
- `sample_input.pkl`
- `xgb_model.pkl` (optional)
- `xgb_threshold.pkl` (optional)
- `scaler.pkl` (optional)

If you need to download missing artifacts, set the appropriate environment variables and run `download_models.sh`.

## Dataset

The raw dataset is available here:

- https://drive.google.com/drive/folders/1X0SV3a6HGJURMjDYfPOfJWzK39mpLlMu?usp=sharing

## Running the project

### Start the API

```bash
python model_api.py
```

The API listens on `http://127.0.0.1:5050`.

### Start the dashboard

```bash
streamlit run streamlit_app.py
```

The Streamlit app opens at `http://localhost:8501`.

## Notes

- `model_api.py` uses `MODELS_DIR` to override the model artifact directory.
- If `xgb_model.pkl` is unavailable, the service still runs using Random Forest only.
- The `saved_models/` directory already includes the artifacts required for the dashboard.
