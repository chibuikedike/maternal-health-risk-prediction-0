# Maternal Health Risk Prediction

A Streamlit application that estimates maternal health risk from six clinical inputs and explains the prediction with a SHAP-based feature contribution chart.

## Overview

This project packages a trained `RandomForestClassifier` inside a Streamlit interface for quick risk screening. A user enters patient vital signs, the app predicts a risk class, displays confidence scores for all classes, and generates a downloadable PDF summary with optional clinical notes.

## Features

- Predicts maternal health risk from six patient measurements
- Shows class confidence for low, mid, and high risk outcomes
- Visualizes model reasoning with SHAP feature contributions
- Exports a PDF report with patient inputs, prediction results, and notes
- Uses a cached local `joblib` model for fast repeat inference

## Model Inputs

The app expects the following features:

- `Age`
- `SystolicBP`
- `DiastolicBP`
- `BS`
- `BodyTemp`
- `HeartRate`

## Tech Stack

- Python
- Streamlit
- scikit-learn
- SHAP
- pandas
- NumPy
- matplotlib
- fpdf2

## Project Structure

```text
.
|-- data/
|-- elite_medical_rf_model.joblib
|-- requirements.txt
|-- streamlit_app.py
`-- README.md
```

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/chibuikedike/maternal-health-risk-prediction-0.git
cd maternal-health-risk-prediction-0
```

### 2. Create and activate a virtual environment

Windows PowerShell:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the app

```bash
streamlit run streamlit_app.py
```

Then open the local Streamlit URL shown in your terminal, usually `http://localhost:8501`.

## How It Works

1. The app loads a serialized scikit-learn pipeline from `elite_medical_rf_model.joblib`.
2. User-provided vital signs are assembled into a pandas DataFrame.
3. The model predicts probabilities for the three risk classes.
4. A SHAP explanation is generated from the classifier to show feature impact.
5. A PDF report can be downloaded with the prediction summary and entered notes.

## Notes

- The included model file is required for the app to run.
- The app is intended for educational and demonstration purposes only.
- If you see a scikit-learn version warning while loading the model, it means the model was serialized with a different scikit-learn version than the one currently installed.

## Disclaimer

This application does not provide medical advice. It is a machine learning demo and must not replace qualified clinical assessment, diagnosis, or treatment.

## License

This repository includes a `LICENSE` file. See it for usage terms.
