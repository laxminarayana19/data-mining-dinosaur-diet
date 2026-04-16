# Predicting Dinosaur Diet from Physical Characteristics
### Data Mining Project — April 2026
**Author:** Laxmi Narayana Gugulothu | **Student ID:** 24180164
**Module:** 7PAM2005 | University of Hertfordshire

---

## Science Question

> *Can we accurately predict a dinosaur's dietary category (carnivore, herbivore, omnivore) based on its physical type, body size, geological period, and geographic location?*

When direct dietary fossil evidence — such as tooth marks, gut contents, or coprolites — is unavailable, a reliable classifier lets palaeontologists make data-driven dietary estimates from routinely recorded physical attributes alone.

---

## Project Structure

```
├── 24180164_Data_Mining_Policy_Summary_Project.ipynb   # Main analysis notebook
├── dino.csv                                             # Dataset
└── README.md
```

---

## Notebook Overview

The notebook is organised into 14 clearly labelled sections:

| # | Section | Description |
|---|---------|-------------|
| 1 | Imports & Configuration | Libraries, plot settings, colour palette |
| 2 | Data Loading & Cleaning | Fix malformed rows, parse length, impute missing values |
| 3 | Feature Engineering | Extract era, sub-period, age (Mya), continent |
| 4 | EDA — Diet Distribution | Class balance check (pie + bar chart) |
| 5 | EDA — Body Length Analysis | Boxplot + mean length by dinosaur type |
| 6 | EDA — Geological Time | Diet patterns across Triassic, Jurassic, Cretaceous |
| 7 | EDA — Geographic Distribution | Fossil discoveries by continent |
| 8 | EDA — Diet by Type (Heatmap) | Diet % breakdown per dinosaur type |
| 9 | Model Training | Random Forest Classifier with hyperparameter justification |
| 10 | Model Evaluation | Confusion matrix |
| 11 | Feature Importances | Mean Decrease in Impurity per feature |
| 12 | Cross-Validation | 5-fold CV accuracy by fold |
| 13 | Predicted Probabilities | Confidence analysis per diet class |
| 14 | Summary & Conclusions | Final metrics and classification report |

---

## Dataset

- **File:** `dino.csv`
- **Source:** Publicly available dinosaur fossil dataset
- **Key columns:** `name`, `diet`, `period`, `lived_in`, `type`, `length`
- **Target variable:** `diet` — three classes: `carnivorous`, `herbivorous`, `omnivorous`

---

## Methods

### Data Cleaning
- Fixed a malformed row where a length value (`1.0m`) was incorrectly placed in the `type` column
- Parsed the `length` column (string format e.g. `"12m"`) into a numeric `length_m` column
- Imputed missing lengths using **group median** (grouped by dinosaur type)
- Filtered to retain only the three valid diet labels

### Feature Engineering
Four new features were extracted from raw text columns:

| Feature | Source | Description |
|---------|--------|-------------|
| `era` | `period` | Triassic, Jurassic, or Cretaceous |
| `sub_period` | `period` | Early, Middle, or Late |
| `age_mya` | `period` | Midpoint age in millions of years |
| `continent` | `lived_in` | Mapped continent from country/region text |

### Model — Random Forest Classifier
- **Train/test split:** 80/20 stratified
- **Cross-validation:** 5-fold
- **Key hyperparameters:**

| Parameter | Value | Reason |
|-----------|-------|--------|
| `n_estimators` | 200 | More trees → more stable predictions |
| `max_depth` | 8 | Limits overfitting |
| `class_weight` | `balanced` | Compensates for class imbalance |
| `random_state` | 42 | Reproducibility |

---

## Key Figures

| Figure | Description |
|--------|-------------|
| Figure 1 | Diet distribution — pie + bar chart |
| Figure 2 | Body length by diet (boxplot) and by type (bar chart) |
| Figure 3 | Diet patterns across geological eras |
| Figure 4 | Dinosaur discoveries by continent |
| Figure 5 | Diet percentage by dinosaur type (heatmap) |
| Figure 6 | Confusion matrix |
| Figure 7 | Feature importances |
| Figure 8 | 5-fold cross-validation accuracy by fold |
| Figure 9 | Mean predicted probabilities by actual diet class |

---

## How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/dinosaur-diet-classification.git
   cd dinosaur-diet-classification
   ```

2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```

3. Place `dino.csv` in the same directory as the notebook.

4. Open and run the notebook:
   ```bash
   jupyter notebook 24180164_Data_Mining_Policy_Summary_Project.ipynb
   ```
   Or open directly in [Google Colab](https://colab.research.google.com/).

---

## Requirements

```
pandas
numpy
matplotlib
seaborn
scikit-learn
```

---

## Academic Context

This project was submitted as part of the **Data Mining "Policy Summary" Project** assessment for module **7PAM2005** at the University of Hertfordshire (April 2026).

---

## License

This repository is for academic submission purposes only.
