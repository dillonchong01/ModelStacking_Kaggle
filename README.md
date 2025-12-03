# Kaggle Competition – Season 5 Episode 11  
**Predicting Loan Payback**

**Task:** Binary classification → predict the probability that a loan will be paid back  
🔗 **Competition link**: https://www.kaggle.com/competitions/playground-series-s5e11/overview

---

## 🎯 Project Goal

The goal of this project was to experiment with **stacking techniques** using multiple models in a meta-learning setup. Instead of relying on a single model, the focus was on **combining the strengths of different algorithms** to improve overall performance and robustness.

---

## 🧠 Models Used

**Base (Level-0) models:**
- XGBoost (Extreme Gradient Boosting)
- LightGBM (Light Gradient Boosting Machine)
- CatBoost (Categorical Boosting)

**Meta (Level-1) model:**
- Logistic Regression

---

## 🔬 Approach

1. Load and preprocess the data

2. Perform feature engineering:
   - Target encoding  
   - Frequency encoding  
   - Quantile binning  

3. Train each base (Level-0) model and generate **out-of-fold (OOF) predicted probabilities** on the training data

4. Combine these predictions into a new dataset, where each column represents the prediction of one base model

5. Train a **Logistic Regression meta (Level-1) model** using this stacked dataset and the original target labels  
   - The meta-model learns how to best weight and combine the base models’ predictions

6. Use the trained base models + meta-model to generate the **final probability predictions** on the test set for submission

---

## 📊 Model Performance (AUC)

- **CatBoost**: 0.92041  
- **LightGBM**: 0.92342  
- **XGBoost**: 0.92466  
- **Overall Meta Model (Stacked)**: **0.92518**

The stacked model achieved the highest AUC, confirming that combining multiple models helped capture complementary patterns in the data.

---

> In a more advanced setup, a wider variety of model types (e.g. neural networks, SVMs) could be included to increase diversity. However, this project was focused on understanding the fundamentals / mechanics of stacking, rather than getting the best possible evaluation metric.
