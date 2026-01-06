# 🌲 Random Forest Classifier

## 🔷 1. What is Random Forest?

**Random Forest** is a **supervised ensemble learning algorithm** used for **classification and regression**.

It builds **multiple decision trees** and combines their predictions to produce a **more accurate and robust model**.

### 🎯 Goal
To reduce **overfitting**, **variance**, and **prediction error** by aggregating many weak learners (decision trees).

📌 For classification:
- Each tree votes for a class
- Final output = **majority vote**

---

## 🔷 2. Why Random Forest Instead of a Single Decision Tree?

### Problems with a Single Decision Tree
- High variance
- Overfits training data
- Sensitive to noise and outliers

### Random Forest Solution
- Uses **bagging (Bootstrap Aggregation)**
- Introduces **feature randomness**
- Produces **decorrelated trees**

📌 Ensemble of weak trees → **strong classifier**

---

## 🔷 3. How Random Forest Works (Step-by-Step)

1️⃣ Draw **bootstrap samples** from the training dataset  
2️⃣ Train a **decision tree** on each sample  
3️⃣ At each split, consider only a **random subset of features**  
4️⃣ Grow trees to maximum depth (usually unpruned)  
5️⃣ Aggregate predictions using **majority voting**

---

## 🔷 4. Decision Tree Foundation

Each tree in a random forest:
- Uses **recursive binary splitting**
- Splits data based on **impurity measures**

### Common Split Criteria
- **Gini Impurity**
\[
Gini = 1 - \sum p_i^2
\]

- **Entropy**
\[
Entropy = -\sum p_i \log_2(p_i)
\]

The split that **maximizes information gain** is chosen.

---

## 🔷 5. Bagging (Bootstrap Aggregation)

### 📌 Bootstrap Sampling
- Sampling **with replacement**
- Each tree sees a slightly different dataset

### 📌 Aggregation
- Classification → Majority vote  
- Regression → Mean prediction  

📌 Bagging reduces **variance**, not bias.

---

## 🔷 6. Feature Randomness (Key Innovation)

At each split:
- Only **k random features** are considered  
- \( k \ll p \) (total features)

### Typical Values
- Classification: \( \sqrt{p} \)
- Regression: \( p/3 \)

📌 Prevents dominant predictors from controlling all trees  
📌 Increases model diversity

---

## 🔷 7. Mathematical Perspective

### Final Prediction (Classification)
\[
\hat{y} = \text{mode} \{ h_1(x), h_2(x), \dots, h_T(x) \}
\]

Where:
- \( h_t(x) \) → Prediction from t-th tree
- T → Number of trees

---

## 🔷 8. Out-of-Bag (OOB) Error

- About **37% of samples** are not used in each bootstrap sample
- These are called **Out-of-Bag samples**

📌 Used to estimate **generalization error** without a validation set

---

## 🔷 9. Feature Importance

### 📌 Mean Decrease in Impurity (MDI)
- Measures total impurity reduction from a feature

### 📌 Permutation Importance
- Measures performance drop after feature shuffling
- More reliable

📌 Helps in **feature selection and interpretation**

---

## 🔷 10. Hyperparameters (Very Important)

| Parameter | Description |
|---------|------------|
| `n_estimators` | Number of trees |
| `max_depth` | Maximum depth of trees |
| `max_features` | Number of features per split |
| `min_samples_split` | Minimum samples to split |
| `min_samples_leaf` | Minimum samples in leaf |
| `bootstrap` | Use bootstrap sampling |

---

## 🔷 11. Handling Class Imbalance

- `class_weight = "balanced"`
- Adjust decision threshold
- Use precision-recall metrics

📌 Random Forest handles imbalance better than many models, but still needs tuning.

---

## 🔷 12. Evaluation Metrics (Classification)

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion Matrix

---

## 🔷 13. Strengths

✔ High accuracy  
✔ Handles non-linear relationships  
✔ Robust to noise and outliers  
✔ Works well with high-dimensional data  
✔ Minimal preprocessing required  

---

## 🔷 14. Limitations

❌ Less interpretable than single trees  
❌ Computationally expensive  
❌ Large memory usage  
❌ Bias toward features with many levels  

---

## 🔷 15. Random Forest vs Other Models

| Aspect | Random Forest | Logistic Regression |
|-----|---------------|-------------------|
| Interpretability | Medium | High |
| Non-linearity | Yes | No |
| Feature scaling | Not required | Required |
| Overfitting | Low | Moderate |
| Use case | Prediction | Inference |

---

