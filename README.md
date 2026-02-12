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



