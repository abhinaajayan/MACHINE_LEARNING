# 🌳 Decision Tree 

## 1️⃣ What is a Decision Tree?

A **Decision Tree** is a **non-parametric, supervised learning algorithm** that learns a hierarchical set of decision rules to map input features (**X**) to an output variable (**y**).

**Formally:**
[ f : X \rightarrow y ]

**Key characteristics:**

* **Non-parametric** → No assumption about data distribution
* **Rule-based** → If–Else conditions
* **Greedy algorithm** → Chooses the best split at each step

---

## 2️⃣ Structure of a Decision Tree

| Component         | Meaning                              |
| ----------------- | ------------------------------------ |
| **Root Node**     | First split (most important feature) |
| **Internal Node** | Feature-based decision               |
| **Branch**        | Outcome of a condition               |
| **Leaf Node**     | Final prediction                     |

---

## 3️⃣ How a Decision Tree Learns

Decision Trees use **recursive binary partitioning**.

**Step-by-step learning:**

1. Start with all data at the root node
2. Try all features and all possible split points
3. Select the split that maximizes purity
4. Split the data
5. Repeat until a stopping condition is met

---

## 4️⃣ Splitting Criteria — Mathematical Core

### A️⃣ Classification Trees

#### (a) Entropy

Measures impurity / uncertainty:

[ \text{Entropy} = - \sum p_i \log_2 p_i ]

* **0** → Pure node
* **High value** → Mixed classes

#### (b) Information Gain (IG)

[ IG = Entropy(parent) - \sum w_i \cdot Entropy(child_i) ]

➡️ Choose the split with **maximum Information Gain**

#### (c) Gini Index

[ Gini = 1 - \sum p_i^2 ]

* Faster than entropy
* Used by default in **scikit-learn**

---

### B️⃣ Regression Trees

Regression Trees minimize **prediction error**, not class impurity.

#### Mean Squared Error (MSE)

[ MSE = \frac{1}{n} \sum (y_i - \bar{y})^2 ]

* Split chosen to minimize **weighted MSE**
* Leaf node prediction = **mean value** of samples in that leaf

---

## 5️⃣ Why Decision Trees Can Model Non-Linearity

Decision Trees:

* Split feature space into **rectangular regions**
* Assign constant predictions within each region

**Mathematical form:**

[ f(x) = \sum c_m \cdot I(x \in R_m) ]

Where:

* ( R_m ) = region
* ( c_m ) = class label or mean value

➡️ Enables **piecewise non-linear approximation**

---

## 6️⃣ Decision Tree as a Weak / Strong Learner

* **Shallow tree** → High bias, low variance
* **Deep tree** → Low bias, high variance (overfitting)

### Bias–Variance Tradeoff

| Tree Depth | Bias | Variance |
| ---------- | ---- | -------- |
| Shallow    | High | Low      |
| Deep       | Low  | High     |

---

## 7️⃣ Overfitting — The Biggest Issue

### Why it happens

* Tree keeps splitting until leaves are pure
* Memorizes noise instead of learning patterns

### Control Methods (Pruning)

| Method                  | Meaning                   |
| ----------------------- | ------------------------- |
| `max_depth`             | Limit tree height         |
| `min_samples_split`     | Minimum samples to split  |
| `min_samples_leaf`      | Minimum samples in a leaf |
| Cost-complexity pruning | Penalizes tree depth      |

---

## 8️⃣ Optimization Problem

* Globally optimal decision tree learning is **NP-Hard**
* Uses **greedy local optimization**

➡️ Best split at each node **does not guarantee** the globally optimal tree

**Therefore:**

* Ensemble models outperform single trees

---

## 9️⃣ Decision Tree vs Linear Models

| Aspect              | Decision Tree | Linear Regression    |
| ------------------- | ------------- | -------------------- |
| Assumptions         | None          | Linearity, normality |
| Feature interaction | Automatic     | Manual               |
| Scaling             | Not needed    | Required             |
| Interpretability    | High          | Medium               |

---

## 🔟 Decision Tree in Feature Selection

Decision Trees perform **implicit feature selection**:

* Important features appear near the root
* Unimportant features may not appear

**Feature Importance:**

[ Importance = \sum (Impurity\ Reduction) ]

---

## 1️⃣1️⃣ Handling Different Data Types

✔ Numerical features
✔ Categorical features (encoded)
✔ Missing values (via surrogate splits)

❌ No need for:

* Normalization
* Standardization

---

## 1️⃣2️⃣ Decision Tree in an ML Pipeline

```
Raw Data
   ↓
Feature Engineering
   ↓
Decision Tree Model
   ↓
Prediction
```

---

## 1️⃣3️⃣ Evaluation Metrics

### Classification

* Accuracy
* Precision
* Recall
* F1-Score
* ROC–AUC

### Regression

* RMSE
* MAE
* R²

---


