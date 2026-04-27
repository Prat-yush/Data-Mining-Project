# 🔋 Early Prediction of Battery Life Using Machine Learning (MICH Dataset)

## 📌 Overview

This project investigates the problem of **early prediction of battery cycle life** using machine learning and deep learning techniques. Battery degradation is a complex, nonlinear, and time-dependent process, making accurate lifetime estimation challenging.

The main objective of this work is to determine whether **early-cycle discharge behavior contains sufficient signal to predict total battery lifetime**, and whether **sequence-based models improve predictive performance compared to classical approaches**.

We analyze the **MICH subset** of the *BatteryLife_Processed* dataset and build predictive models ranging from simple baselines to LSTM-based sequence models.

---

## 👉 Start here: main_notebook.ipynb

## 🎥 Project Video
https://www.youtube.com/watch?v=zmX2V_1Slzo

---

## 📂 Dataset

This project uses the **MICH subset** of the BatteryLife dataset:

📌 **Source:**  
Tan et al. (2025), *BatteryLife: A Comprehensive Dataset and Benchmark for Battery Life Prediction*  
🔗 https://doi.org/10.5281/zenodo.17958489

### 📁 Data Components

- **Battery time-series files (`.pkl`)**
  - Per-cycle charge/discharge measurements
  - Includes voltage, current, and capacity signals
- **Life labels (`total_MICH_labels.json`)**
  - Maps each battery ID to total cycle life (target variable)

### 🔧 Data Characteristics

- Variable-length time-series per battery
- Strong heterogeneity in degradation patterns
- Significant variation in initial capacity and lifetime
- Nonlinear capacity fade behavior

---

## 📊 Exploratory Data Analysis (EDA)

The dataset was analyzed to understand structural and statistical properties:

### Key analyses:
- Distribution of battery cycle life
- Early-cycle capacity trends
- Capacity degradation curves over time
- Variability across batteries

### 🔎 Key Insights:

- Battery lifetimes vary significantly across samples
- Degradation behavior is highly nonlinear
- Early cycles show measurable but noisy predictive signals
- Strong inter-battery variability suggests the need for robust modeling approaches

These findings motivate both **feature-based models** and **sequence-based deep learning approaches**.

---

## 🤖 Modeling Approach

### 🎯 Prediction Task

The goal is to predict:

> **Remaining Useful Life (RUL)** or total cycle life of a battery using early-cycle information.

---

### 🧠 Models Implemented

This project evaluates multiple modeling strategies:

#### 📌 Classical Machine Learning Models
- k-Nearest Neighbors Regression (k-NN)
- Random Forest Regression

These models operate on **engineered early-cycle features** such as average discharge capacity.

#### 📌 Sequence-Based Model
- Long Short-Term Memory (LSTM) neural network

The LSTM directly processes **early-cycle time-series sequences**, allowing it to capture temporal degradation dynamics.

---

### ⚙️ Design Decisions

- Early-cycle windows used as predictive input (3, 5, 10 cycles)
- Feature extraction from discharge capacity signals
- Train/test split performed at battery level (to avoid leakage)
- Evaluation metrics:
  - Mean Absolute Error (MAE)
  - Root Mean Squared Error (RMSE)

---

## 🔬 Research Questions (Checkpoint 2)

This project is structured around three core research questions:

### ❓ RQ1
How accurately can early-cycle battery measurements predict total cycle life using classical regression models?

### ❓ RQ2
How does increasing the amount of early-cycle data affect prediction accuracy for battery lifetime estimation?

### ❓ RQ3
Do sequence-based deep learning models (LSTM) outperform classical machine learning models in capturing degradation dynamics?

---

## 🧪 Method Feasibility Testing

Before full model development, feasibility tests were conducted to validate data usability and pipeline correctness.

### Feature Engineering Test
A simple early-cycle feature was constructed:

- Mean discharge capacity over initial cycles

This provides a compact representation of early degradation behavior.

---

### Baseline Model Tests

Two classical models were tested:

- Random Forest Regression
- k-Nearest Neighbor Regression

### Outcomes:

- Dataset successfully converted into supervised learning format
- Models trained without preprocessing issues
- Early-cycle features show measurable predictive signal

These results confirm the **feasibility of applying machine learning techniques to the dataset**.

---

## 📈 Experimental Pipeline Summary

The full modeling pipeline includes:

1. Data loading and preprocessing
2. Feature extraction from early-cycle signals
3. Baseline regression modeling (k-NN, Random Forest)
4. Sequence construction for LSTM
5. Deep learning model training
6. Evaluation using MAE and RMSE
7. Comparative analysis across models

---

## 📊 Key Results Summary

Across experiments, the following patterns were observed:

- Early-cycle data contains meaningful predictive signal for battery life
- Random Forest consistently outperforms k-NN among classical models
- LSTM achieves the strongest performance overall by capturing temporal structure
- Increasing early-cycle window size shows diminishing returns in predictive accuracy

---

## 🧠 Final Insight

The results suggest that:

> Battery degradation is partially predictable from early behavior, but the effectiveness of prediction depends heavily on how temporal information is modeled.

Classical machine learning models perform strongly with engineered features, while sequence-based models provide additional gains by directly learning from time-series structure.

---

## 📦 Reproducibility

This project was developed in **Google Colab**.

To reproduce:
pip install -r requirements.txt

## ⚙️ Key Dependencies and Versions

This project was developed using the following core libraries:

- **Python:** 3.10+
- **NumPy:** 1.26.x
- **pandas:** 2.2.x
- **scikit-learn:** 1.4.x
- **PyTorch:** 2.2.x
- **Matplotlib:** 3.8.x
- **SciPy:** 1.11.x
- **tqdm:** 4.66.x

These libraries support data processing, machine learning, visualization, and deep learning components of the project.
The full dependency list is available in `requirements.txt`.


## 📊 Results Summary

This project shows that early-cycle battery data contains meaningful predictive signal for estimating total cycle life.

Key findings include:
- Classical models (Random Forest) outperform simpler baselines like k-NN
- Sequence-based modeling (LSTM) achieves the strongest overall performance
- Increasing early-cycle window size improves performance initially, but shows diminishing returns

### 🔑 Key Insight:
Battery degradation patterns can be partially captured early in the lifecycle, but best performance is achieved when temporal structure is explicitly modeled using sequence-based approaches.



