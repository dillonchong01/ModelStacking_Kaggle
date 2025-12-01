# Kaggle Competition  -  Season 5 Episode 11 
**Predicting Loan Payback**

Task: Binary classification → **predict the probability** that a loan will be paid back

🔗 **Competition link**: https://www.kaggle.com/competitions/playground-series-s5e11/overview

---

## 🎯 Project Goal

The personal goal for this competition was to experiment with **stacking techniques** using multiple models through a meta-learning approach.

Instead of relying on a single model, this project focused on integrating multiple learners to improve predictive performance and model robustness.

---

## 🧠 Models Used

**Base (Level-0) models:**
- **XGBoost** (Extreme Gradient Boosting)
- **LightGBM** (Light Gradient Boosting Machine)
- **CatBoost** (Categorical Boosting)
- **Histogram Gradient Boosting (HGB)** from scikit-learn

**Meta (Level-1) model:**
- **Logistic Regression**

---

## 🔬 Approach

1. Load and preprocess the data

2. Perform feature engineering:
   - Target encoding  
   - Frequency encoding  
   - Quantile binning  

3. Use **Optuna** to tune hyperparameters for each base (Level-0) model:
   - XGBoost, LightGBM, CatBoost, HistogramGB

4. Train the base models and generate **out-of-fold (OOF) predicted probabilities** on the training data

5. Combine these predictions into a new dataset, where each column comes from the prediciton of one base model:


6. Train a **Logistic Regression meta (Level-1) model** using this new dataset and the original target labels. The meta-model learns how to best combine the base models’ predictions

7. Use the trained base models + meta-model together (on the full dataset) to produce the **final probability predictions** on the test set for submission

---

> In a more advanced setup, a wider variety of model types (e.g. neural networks, SVMs, etc.) could have been included to increase model diversity in the stack. However, this project was mainly aimed at understanding the fundamentals and mechanics of stacking, so I did not focus on incorporating diverse model types.

---