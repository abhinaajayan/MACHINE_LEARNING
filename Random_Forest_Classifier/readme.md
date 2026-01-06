# 🌲 Random Forest Classifier

## 1️⃣ What is a Random Forest?

A **Random Forest Classifier** is an **ensemble learning algorithm** that builds multiple decision trees and combines their predictions using **majority voting**.

### Formal Definition

\[
\hat{y} = \text{mode}\{h_1(x), h_2(x), ..., h_T(x)\}
\]

Where:
- \( h_t(x) \) = prediction of the *t-th decision tree*
- \( T \) = total number of trees

**Key idea:**  
> Many weak, uncorrelated trees together form a strong classifier.

---

## 2️⃣ Why Random Forest Was Needed 

### Problems with Decision Trees
- High variance
- Overfitting
- Sensitive to noise and small data changes

### Solution
Random Forest reduces variance using:
- **Bootstrap Aggregation (Bagging)**
- **Random Feature Selection**

---

## 3️⃣ Two Sources of Randomness

### A️⃣ Bootstrap Sampling (Bagging)
- Sampling **with replacement**
- Each tree sees a different dataset

If dataset size = **N**:
- ~63% unique samples
- ~37% left out → **Out-Of-Bag (OOB) samples**

---

### B️⃣ Random Feature Subspace
At each split:
- Consider only **√p features** (for classification)
- Instead of all **p features**

**Why?**
- De-correlates trees
- Prevents dominance of strong predictors
- Improves generalization

---

## 4️⃣ Algorithm — Step by Step

1. Draw a bootstrap sample from training data
2. Train a decision tree:
   - No pruning
   - Random subset of features at each split
3. Repeat steps 1–2 for **T trees**
4. Prediction:
   - Each tree predicts a class
   - Final output = **majority vote**

---

## 5️⃣ Mathematical Intuition (Variance Reduction)

If variance of one tree = \( \sigma^2 \)

\[
Var_{RF} \approx \rho \sigma^2 + \frac{1 - \rho}{T} \sigma^2
\]

Where:
- \( \rho \) = correlation between trees
- \( T \) = number of trees

➡️ Lower correlation + more trees = lower variance

---

## 6️⃣ Splitting Criteria (Inside Each Tree)

Random Forest uses **CART (Classification and Regression Trees)**:
- **Gini Index** (default)
- **Entropy** (optional)

Each tree is grown **fully (unpruned)**.

---

## 7️⃣ Bias–Variance Tradeoff

| Model | Bias | Variance |
|-----|-----|-----|
| Decision Tree | Low | High |
| Random Forest | Slightly higher | Much lower |

➡️ Random Forest trades **a small increase in bias** for a **large reduction in variance**.

---

## 8️⃣ Overfitting in Random Forest

- Rare compared to single decision trees
- Increasing trees generally **does not cause overfitting**

Overfitting may occur when:
- Data is extremely noisy
- Dataset is very small with very deep trees

---

## 9️⃣ Feature Importance

Random Forest provides built-in feature importance measures.

### A️⃣ Mean Decrease in Impurity (MDI)
\[
Importance = \sum \text{Gini Reduction}
\]

⚠ Can be biased toward continuous features

---

### B️⃣ Permutation Importance (Preferred)
- Shuffle a feature
- Measure drop in model accuracy
- More reliable and model-agnostic

---

## 🔟 Out-Of-Bag (OOB) Error

- Uses leftover (~37%) samples
- Acts like internal cross-validation
- No separate validation set needed

```python
RandomForestClassifier(oob_score=True)

---

## 1️⃣1️⃣ Important Hyperparameters

| Parameter | Description |
|----------|------------|
| `n_estimators` | Number of trees in the forest |
| `max_depth` | Maximum depth of each tree (controls overfitting) |
| `max_features` | Number of features considered at each split |
| `min_samples_leaf` | Minimum samples required in a leaf node (smooths predictions) |
| `class_weight` | Handles class imbalance by assigning weights |

---

## 1️⃣2️⃣ Evaluation Metrics (Classification)

- **Accuracy** – Overall correctness of the model  
- **Precision** – Correct positive predictions out of all predicted positives  
- **Recall** – Correct positive predictions out of all actual positives  
- **F1-Score** – Harmonic mean of precision and recall  
- **ROC-AUC** – Ability of the model to distinguish between classes  
- **Confusion Matrix** – Summary of true vs predicted classifications  

---

## 1️⃣3️⃣ Strengths of Random Forest

✔ Handles complex non-linear relationships  
✔ Robust to noise and outliers  
✔ No feature scaling or normalization required  
✔ Works well with mixed data types (numerical + categorical)  
✔ Excellent baseline model for classification tasks  

---

## 1️⃣4️⃣ Limitations of Random Forest

❌ Less interpretable compared to a single decision tree  
❌ High memory usage due to multiple trees  
❌ Slower prediction for very large forests  
❌ Poor extrapolation beyond the training data range  

---

