# Home Credit Default Risk — ML Pipeline

> End-to-end supervised ML pipeline for credit default prediction using Home Credit's 7-table relational dataset. Covers feature engineering, 5-model comparison, SHAP explainability, and FastAPI + Docker MLOps deployment.

**Academic context:** NIB 7072 Machine Learning — MSc Data Science, Coventry University / NIBM Sri Lanka (2025)  
**Portfolio context:** Designed as a Data Engineer portfolio project demonstrating production-grade ML pipeline design.

---

## Problem Statement

Home Credit Group provides loans to people with limited or no credit history. The objective is to predict whether a loan applicant will default on repayment (TARGET=1) or repay successfully (TARGET=0).

| Property | Value |
|---|---|
| Dataset | Home Credit Default Risk (Kaggle Competition) |
| Training instances | 307,511 |
| Features (main file) | 122 |
| Auxiliary tables | 6 (bureau, bureau_balance, previous_application, POS_CASH_balance, credit_card_balance, installments_payments) |
| Target | Binary — 0: repaid, 1: default |
| Class imbalance | 91.93% repaid vs 8.07% default |
| Total dataset size | ~2.7 GB |

---

## Project Structure

```
ml_home_credit_default/
│
├── notebooks/                          # CW submission — exploratory analysis
│   ├── 01_data_understanding.ipynb     # Task 1: Dataset overview & literature review
│   ├── 02_eda_feature_engineering.ipynb# Task 2: EDA, missing values, feature engineering
│   ├── 03_model_development.ipynb      # Task 3: 5 models + hyperparameter tuning
│   ├── 04_evaluation.ipynb             # Task 4: Metrics, comparison, error analysis
│   ├── 05_explainability.ipynb         # Task 5: SHAP, LIME, fairness & ethics
│   └── 06_mlops_architecture.ipynb     # Task 6: Cloud deployment & MLOps design
│
├── src/                                # Production code — DE portfolio
│   ├── pipeline/
│   │   ├── data_loader.py              # ETL: loads and validates all 7 tables
│   │   ├── feature_engineering.py      # Reusable feature transforms
│   │   └── preprocessing.py           # Imputation, encoding, scaling
│   ├── models/
│   │   ├── trainer.py                  # Training loop with CV + Bayesian HPO
│   │   └── evaluator.py               # Metrics, plots, model comparison
│   └── monitoring/
│       └── drift_detector.py           # Data drift and concept drift detection
│
├── app/                                # Deployable inference service
│   ├── main.py                         # FastAPI REST endpoint
│   └── schemas.py                      # Pydantic request/response schemas
│
├── airflow/
│   └── home_credit_dag.py              # Retraining orchestration DAG
│
├── tests/
│   └── test_pipeline.py                # Unit tests for pipeline modules
│
├── outputs/
│   ├── figures/                        # Generated plots
│   ├── models/                         # Saved model artifacts
│   └── reports/                        # Evaluation reports
│
├── .gitignore
├── requirements.txt
└── README.md
```

---

## ML Pipeline Tasks (CW Q1 — 40 marks)

| Task | Description | Marks |
|---|---|---|
| 1. Dataset Understanding | Source, attributes, literature review (6 papers), research gap | 10% |
| 2. EDA & Feature Engineering | Visualisations, correlations, 4+ new features, PCA/importance | 15% |
| 3. Model Development | Logistic Regression, KNN, Random Forest, LightGBM, ANN + Bayesian HPO | 25% |
| 4. Evaluation | Accuracy, Precision, Recall, F1, ROC-AUC, PR-AUC, error analysis | 15% |
| 5. Explainability & Ethics | SHAP, LIME, fairness analysis, bias discussion | 10% |
| 6. Cloud Deployment & MLOps | Docker, FastAPI, CI/CD, drift detection, retraining strategy | 25% |

---

## Tech Stack

| Layer | Technologies |
|---|---|
| Data processing | Python, Pandas, NumPy |
| Visualisation | Matplotlib, Seaborn, Plotly |
| Machine learning | Scikit-learn, LightGBM, XGBoost, CatBoost |
| Deep learning | TensorFlow / Keras |
| Imbalance handling | imbalanced-learn (SMOTE) |
| Hyperparameter tuning | Optuna (Bayesian optimisation) |
| Explainability | SHAP, LIME |
| API serving | FastAPI, Uvicorn |
| Containerisation | Docker |
| Orchestration | Apache Airflow |
| CI/CD | GitHub Actions |

---

## Setup

```bash
# Clone the repository
git clone <repo-url>
cd ml_home_credit_default

# Run virtual environment
python -m venv venv
source venv/bin/activate  # Mac/Linux
venv\Scripts\activate     # Windows

# Install dependencies
pip install -r requirements.txt

# Download dataset
# Place all CSV files from Kaggle into: ../q1_dataset/
# https://www.kaggle.com/competitions/home-credit-default-risk/data

# Launch notebooks
jupyter notebook notebooks/
```

---

## Status

- [x] Project structure setup
- [x] Task 1: Data understanding & literature review
- [ ] Task 2: EDA & feature engineering
- [ ] Task 3: Model development
- [ ] Task 4: Evaluation
- [ ] Task 5: Explainability
- [ ] Task 6: MLOps deployment

---

*MSc Data Science — Coventry University / NIBM Sri Lanka, 2025*
