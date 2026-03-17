# 🔋 Battery Life Prediction – MICH Dataset

## 📌 Overview

This project performs Exploratory Data Analysis (EDA) and Remaining Useful Life (RUL) prediction using the **MICH subset** of the *BatteryLife_Processed* dataset.

The goal is to analyze battery degradation behavior and build predictive models for cycle life estimation.

**Dataset Source:**  
Tan et al. (2025), *BatteryLife: A Comprehensive Dataset and Benchmark for Battery Life Prediction*  
DOI: https://doi.org/10.5281/zenodo.17958489

---

## 📂 Dataset Used

- Subset: **MICH**
- Battery files: `.pkl`
- Life labels: `total_MICH_labels.json`

Each battery file contains:
- Metadata (materials, voltage limits, protocols, etc.)
- `cycle_data` (per-cycle time-series measurements)


---

## 📊 Exploratory Data Analysis (EDA)

The following analyses were performed:

- Distribution of cycle life
- Sequence length distribution
- Capacity degradation curves
- Initial capacity variability

### 🔎 Key Observations

- Significant variability in cycle life across batteries  
- Variable-length degradation sequences  
- Nonlinear capacity fade behavior  
- Differences in initial capacity across cells  

These findings motivate the use of nonlinear time-series models.

---

## 🤖 Modeling Approach

### 🎯 Target
Predict **Remaining Useful Life (RUL)**.

### 🧠 Models Implemented
- **Linear Regression** (baseline, interpretable)
- **LSTM** (sequence-based deep learning model)

### ⚙️ Design Decisions

- Normalize capacity by initial value  
  → Reduces inter-battery variability  

- Split data by battery (not by cycle)  
  → Prevents data leakage  

- Use MAE and RMSE for evaluation  
  → Appropriate for continuous prediction

  ---

## 🔬 Research Question Formation (Checkpoint 2)

Checkpoint 2 focuses on transforming the initial exploratory findings into concrete research questions and validating the feasibility of the proposed modeling methods.

### ❓ Research Questions

**RQ1:**  
How accurately can early-cycle battery measurements predict total cycle life using classical regression models?

**RQ2:**  
How does the amount of early-cycle data used for prediction affect the accuracy of remaining useful life estimation?

**RQ3:**  
Do sequence-based models capture degradation patterns that improve prediction accuracy compared to classical machine learning approaches?

---

## 🧪 Initial Method Feasibility Tests

Before implementing the full modeling pipeline, small feasibility experiments were conducted to ensure that the proposed algorithms and libraries can be applied successfully to the dataset.

### Feature Extraction Test

A simple feature was extracted from the dataset:

- **Early-cycle capacity feature:**  
  Average discharge capacity from the first few cycles of each battery.

This feature provides a simple signal representing early degradation behavior.

### Baseline Algorithm Tests

Two regression models were tested using the extracted feature:

- **Random Forest Regression**
- **k-Nearest Neighbor Regression**

These experiments confirmed that:

- Battery cycle data can be successfully processed into usable features  
- Machine learning models can be trained on the dataset  
- The selected Python libraries (pandas, scikit-learn) work correctly with the project data

These runs serve as **method feasibility checks**, not final model evaluations.

---

## 📈 Next Steps

Future stages of the project will extend this work by:

- Extracting richer early-cycle features from the battery time-series data
- Training multiple regression and sequence-based models
- Comparing classical machine learning models with deep learning approaches
- Evaluating model performance using MAE and RMSE

The final goal is to determine which modeling strategies best capture battery degradation patterns and provide accurate predictions of battery cycle life.




