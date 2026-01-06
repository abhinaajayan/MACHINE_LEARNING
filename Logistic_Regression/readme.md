# 📘 Logistic Regression

## 🔷 1. What is Logistic Regression?

**Logistic Regression** is a **supervised statistical learning method** used to model the relationship between:

- **Dependent variable (Y)** → **Categorical (usually binary: 0 or 1)**
- **Independent variables (X)** → One or more predictors (continuous or categorical)

### 🎯 Goal
To estimate the **probability** that an observation belongs to a particular class.

📌 Despite its name, **logistic regression is a classification algorithm**, not a regression algorithm.

---

## 🔷 2. Why Not Linear Regression for Classification?

Linear regression:
- Can predict values < 0 or > 1
- Assumes normally distributed errors
- Violates assumptions for binary outcomes

🔹 Logistic regression solves this by:
- Constraining outputs between **0 and 1**
- Using a **sigmoid (logistic) function**
- Modeling **probabilities instead of raw values**

---

## 🔷 3. Logistic Regression Model

### 📐 Linear Combination
\[
z = \beta_0 + \beta_1 X_1 + \beta_2 X_2 + \cdots + \beta_p X_p
\]

### 📐 Sigmoid (Logistic) Function
\[
P(Y=1 \mid X) = \frac{1}{1 + e^{-z}}
\]

This maps any real value to a **probability between 0 and 1**.

---

## 🔷 4. Odds and Log-Odds (Very Important Concept)

### 📌 Odds
\[
\text{Odds} = \frac{P(Y=1)}{P(Y=0)}
\]

### 📌 Log-Odds (Logit)
\[
\log\left(\frac{P(Y=1)}{1 - P(Y=1)}\right)
= \beta_0 + \beta_1 X_1 + \cdots + \beta_p X_p
\]

📌 Logistic regression models **log-odds as a linear function of predictors**.

---

## 🔷 5. Interpretation of Coefficients

### 🔹 Coefficient (βᵢ)
- Represents the **change in log-odds** for a one-unit increase in Xᵢ
- Holding all other variables constant

### 🔹 Odds Ratio (OR)
\[
OR = e^{\beta_i}
\]

- **OR > 1** → Increases probability of event
- **OR < 1** → Decreases probability of event

**Example:**
> OR = 2 → The odds of mangrove presence are **2 times higher** for a unit increase in NDVI.

---

## 🔷 6. Estimation of Parameters

### 🔹 Maximum Likelihood Estimation (MLE)

Unlike linear regression (OLS), logistic regression uses **MLE**.

### 📐 Likelihood Function
\[
L(\beta) = \prod_{i=1}^{n} P(y_i \mid x_i)
\]

### 📐 Log-Likelihood
\[
\ell(\beta) = \sum_{i=1}^{n}
\left[ y_i \log(p_i) + (1 - y_i)\log(1 - p_i) \right]
\]

🎯 Objective: **Maximize log-likelihood**

---

## 🔷 7. Loss Function

### 📌 Binary Cross-Entropy (Log Loss)
\[
\text{Loss} = - \left[ y \log(p) + (1 - y)\log(1 - p) \right]
\]

- Penalizes confident but wrong predictions
- Convex → guarantees global minimum

---

## 🔷 8. Decision Boundary

- Default threshold: **0.5**
- If \( P(Y=1) \ge 0.5 \) → Class 1
- If \( P(Y=1) < 0.5 \) → Class 0

📌 Threshold can be adjusted for **imbalanced datasets**.

---

## 🔷 9. Assumptions of Logistic Regression

1️⃣ Binary dependent variable  
2️⃣ Independent observations  
3️⃣ Linear relationship between predictors and **log-odds**  
4️⃣ No multicollinearity  
5️⃣ Large sample size preferred  

📌 Logistic regression **does not assume normality or homoscedasticity**.

---

## 🔷 10. Model Evaluation Metrics

### 📊 Classification Metrics
- Accuracy
- Precision
- Recall
- F1-score

### 📊 Probability Metrics
- ROC Curve
- AUC (Area Under Curve)
- Log Loss

### 📊 Confusion Matrix
| Actual / Predicted | 0 | 1 |
|-------------------|---|---|
| 0 | TN | FP |
| 1 | FN | TP |

---

## 🔷 11. Regularization in Logistic Regression

| Method | Purpose |
|------|--------|
| L1 (Lasso) | Feature selection |
| L2 (Ridge) | Handles multicollinearity |
| Elastic Net | L1 + L2 |

---

## 🔷 12. Strengths

✔ Interpretable coefficients  
✔ Probabilistic output  
✔ Efficient and fast  
✔ Strong statistical foundation  

---

## 🔷 13. Limitations

❌ Assumes linearity in log-odds  
❌ Sensitive to outliers  
❌ Cannot capture complex non-linear patterns  
❌ Performance drops with highly overlapping classes  

---

