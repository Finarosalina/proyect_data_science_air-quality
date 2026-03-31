# 🔬 Beyond AQI: Factors Influencing Mortality by Spanish Province

> *"What is essential is invisible to the eye."* — Antoine de Saint-Exupéry

**[🚀 Open the live Streamlit app](https://your-app-url.streamlit.app)**

---

## Overview

Can air quality alone explain mortality rates across Spanish provinces? This project goes beyond the Air Quality Index (AQI) to explore how environmental, sociodemographic, and political variables jointly influence public health outcomes.

Using machine learning and a multidisciplinary approach, we built a classification model that predicts provincial mortality levels (low / medium / high) from a combination of air pollutant data, political context, urban/rural classification, and cause-of-death statistics.

---

## Objectives

- Predict mortality level (3 classes: low, medium, high) at the Spanish province level
- Identify which factors — beyond air quality — drive health outcomes
- Deploy an interactive tool for real-time prediction and exploration

---

## Models

Two models were developed and compared:

| Model | Period | Notes |
|---|---|---|
| **Pre-COVID** *(deployed in app)* | Up to 2019 | Trained on "normal" data, better performance, lower noise |
| **Full dataset** *(analysis only)* | 2013–2022 | Includes COVID impact, higher variability, used for comparative analysis |

---

## Methodology

**1. Data Collection**
- Air quality data: OpenAQ, MITECO
- Mortality by cause: INE (Spanish National Statistics Institute), Ministry of Health
- Political and demographic variables: electoral results, urban/rural classification

**2. Data Processing**
- Aggregation and cleaning of pollutant measurements
- AQI calculation per province and year
- Categorical encoding and normalization
- Target variable `mortality_class` created by tertile split (low / medium / high)

**3. Modeling**
- Random Forest Classifier optimized with GridSearchCV
- Cross-validation for robust performance estimation
- Evaluation: accuracy, F1-score (weighted and macro), classification report

**4. Deployment**
- Interactive Streamlit app with real-time prediction
- User-friendly interface with visualizations
- Pre-COVID model deployed as the production model

---

## Results

- Pre-COVID model achieves strong classification performance with lower variance
- Air quality alone is insufficient to explain mortality — political, demographic, and geographic variables significantly improve predictive power
- Random Forest outperformed baseline models after GridSearchCV optimization

---

## Tech Stack

- **Data** — pandas, numpy, requests
- **Modeling** — scikit-learn (RandomForestClassifier, GridSearchCV)
- **Visualization** — matplotlib, seaborn
- **Deployment** — Streamlit
- **Persistence** — joblib

---

## Project Structure

```
air-quality-politics/
├── app/
│   ├── app.py                      # Streamlit app
│   ├── preprocesamiento.py         # Preprocessing pipeline
│   └── models/
│       └── columnas_modelo.pkl     # Saved model columns
├── data/
│   └── df_procesado.csv            # Processed dataset
├── notebooks/
│   └── 01_exploracion.ipynb        # EDA and model development
├── requirements.txt
└── README.md
```

---

## How to Run

```bash
# Clone the repository
git clone https://github.com/ullaom/air-quality-politics.git
cd air-quality-politics

# Install dependencies
pip install -r requirements.txt

# Launch the app
streamlit run app/app.py
```

**Requirements:** Python 3.8+, streamlit, scikit-learn, pandas, matplotlib, seaborn, joblib, requests

---

## Authors

- **María Pais** — [@Finarosalina](https://github.com/Finarosalina)
- **Ulla Aller**
- **María Miura**

---

## Key Learnings

- AQI is a useful proxy but insufficient as a standalone predictor of mortality outcomes
- Political and urban/rural context adds meaningful signal to environmental health models
- COVID-19 introduced significant noise — separating pre/post-COVID periods improved model stability
- Deploying a pre-COVID model for inference avoids distributional shift from the pandemic period

---

*Developed as part of the 4Geeks Academy Data Science & ML program.*# 🔬 MÁS ALLÁ DEL ICA: Factores que influyen en la mortalidad por provincia

> “Lo esencial es invisible a los ojos.” — Antoine de Saint‑Exupéry

**Accede directamente a la app aquí** 👉 [Abrir aplicación Streamlit](https://air-quality-politics-7zt2ipxuaappvamjddjimw7.streamlit.app/)

