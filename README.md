<h1 align="center">Weather-Sense ML</h1>

<p align="center">
  <strong>C + Python weather condition classifier with a Windows desktop interface.</strong><br>
  Uses a trained Random Forest model to classify weather from temperature, humidity, air pressure, and wind speed.
</p>


<p align="center">
  <img alt="GitHub Repo stars" src="https://img.shields.io/github/stars/AjaySoni-Dev/Weather-Sense-ML?style=social">
  <img alt="GitHub forks" src="https://img.shields.io/github/forks/AjaySoni-Dev/Weather-Sense-ML?style=social">
</p>


<p align="center">
  <img alt="status: educational prototype" src="https://img.shields.io/badge/status-educational%20prototype-blue">
  <img alt="stack: C + Python" src="https://img.shields.io/badge/stack-C%20%2B%20Python-informational">
  <img alt="license: MIT" src="https://img.shields.io/badge/license-MIT-green">
</p>

<p align="center">
  <a href="#overview">Overview</a> ·
  <a href="#implemented-files">Implemented Files</a> ·
  <a href="#how-it-works">How It Works</a> ·
  <a href="#run-locally">Run Locally</a> ·
  <a href="#limitations">Limitations</a>
</p>

---

## Overview

**Weather-Sense ML** is an educational machine-learning project that connects a **C Win32 GUI** with a **Python prediction script**. The repository includes the dataset, a notebook used for training, a saved `RandomForestClassifier`, a saved `LabelEncoder`, and a Windows-style C interface that sends user inputs to the Python script.

The project is not only a weather UI. It demonstrates a small cross-language workflow:

```text
User enters weather values in C GUI
        ↓
C program runs predict.py with numeric inputs
        ↓
Python loads the saved ML model and label encoder
        ↓
Predicted class is returned to the GUI
        ↓
GUI stores the prediction in local session history
```

## What Is Actually Implemented

- A balanced weather dataset with **4,000 rows** and five classes: `Sunny`, `Rainy`, `Stormy`, `Cloudy`, and `Partly Cloudy`.
- A Jupyter notebook that trains and saves a Random Forest model.
- A saved `random_forest_model.pkl` file with **100 estimators**.
- A saved `label_encoder.pkl` file for converting numeric model outputs back into weather labels.
- A Python CLI prediction script that accepts four numeric values.
- A C Win32 GUI with input boxes, predict button, run-again/reset flow, and prediction history.

## Implemented Files

| File | Purpose |
|---|---|
| `main.c` | Windows GUI application built using `windows.h`; collects inputs, runs prediction command, and displays result/history. |
| `predict.py` | Loads model and label encoder, receives command-line values, and prints the predicted weather class. |
| `Jupyter_Notebook_File.ipynb` | Training workflow using pandas, train/test split, label encoding, and Random Forest classification. |
| `weather_data_balanced.csv` | Balanced dataset with temperature, humidity, air pressure, wind speed, and weather condition. |
| `random_forest_model.pkl` | Trained Random Forest model. |
| `label_encoder.pkl` | Saved encoder for class labels. |
| `LICENSE.txt` | MIT license. |

## Tech Stack

| Area | Tools |
|---|---|
| Desktop interface | C, Win32 API |
| ML training | Python, pandas, scikit-learn |
| Model type | Random Forest Classifier |
| Model persistence | pickle |
| Dataset | CSV weather dataset |

## Run Locally

### 1. Install Python libraries

```bash
pip install pandas numpy scikit-learn
```

### 2. Test the prediction script

```bash
python predict.py 25 65 1000 12
```

### 3. Compile the C GUI on Windows

Using MinGW/GCC:

```bash
gcc main.c -o weather_sense.exe
```

### 4. Run the application

```bash
weather_sense.exe
```

## Limitations

- This is an educational classifier, not a real meteorological forecasting system.
- The saved pickle files are tied to the scikit-learn version used during training, so model loading may produce compatibility warnings in newer versions.
- The C GUI is Windows-specific because it uses the Win32 API.
- There is no `requirements.txt` yet; dependencies should be added for easier setup.
- The model is trained on the included dataset only and should not be treated as production-grade weather intelligence.

## Recommended Improvements

- Add `requirements.txt`.
- Add model accuracy metrics from the notebook.
- Add a clean screenshot of the GUI.
- Add error handling for non-numeric inputs.
- Replace pickle with a safer documented persistence workflow if the model is shared widely.

## License

This project is licensed under the MIT License.
