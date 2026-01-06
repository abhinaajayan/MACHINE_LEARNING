# 📘 Linear Regression

## 🔷 1. What is Linear Regression? 

**Linear Regression** is a **supervised statistical learning method** used to model the **linear relationship** between:

- **Dependent variable (Y)** → Continuous  
- **Independent variable(s) (X)** → One or more predictors  

### 🎯 Goal
To find the **best-fitting straight line (or hyperplane)** that predicts **Y from X**.

### 📐 Mathematical Form
\[
Y = \beta_0 + \beta_1 X_1 + \beta_2 X_2 + \cdots + \beta_p X_p + \varepsilon
\]

Where:
- **β₀** → Intercept  
- **βᵢ** → Regression coefficients  
- **ε** → Random error term  

---

## 🔷 2. Simple vs Multiple Linear Regression

### 📌 Simple Linear Regression
\[
Y = \beta_0 + \beta_1 X
\]

**Used when:**
- Only one predictor  
- Easy interpretation  

---

### 📌 Multiple Linear Regression
\[
Y = \beta_0 + \beta_1 X_1 + \beta_2 X_2 + \beta_3 X_3 + \varepsilon
\]

**Used when:**
- Multiple influencing factors  
- Controls confounding variables  

---

## 🔷 3. Mathematical Foundation

### 🎯 Objective
Minimize the **Residual Sum of Squares (RSS)**:

\[
RSS = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
\]

Where:
- **yᵢ** → Actual value  
- **ŷᵢ** → Predicted value  

### 🔹 Ordinary Least Squares (OLS)
OLS estimates coefficients **β** such that the **sum of squared vertical distances** between observed and predicted values is minimized.

---

## 🔷 4. Estimation of Coefficients (OLS Solution)

### 📐 Matrix Form
\[
\hat{\beta} = (X^T X)^{-1} X^T Y
\]

### 💡 Why this matters (Interview Point):
- Shows **linear algebra foundation**
- Explains **multicollinearity**
- If \( X^T X \) is not invertible → coefficients become unstable  

---

## 🔷 5. Assumptions of Linear Regression

Linear regression is valid **only if these assumptions hold**:

1️⃣ **Linearity**  
Relationship between X and Y must be linear  

2️⃣ **Independence**  
Observations must be independent  

3️⃣ **Homoscedasticity**  
Constant variance of residuals  

4️⃣ **Normality of Errors**  
Residuals should follow normal distribution  

5️⃣ **No Multicollinearity**  
Predictors should not be highly correlated  

📌 **Violation of assumptions → biased or unreliable results**

---

## 🔷 6. Model Interpretation

### 🔹 Regression Coefficient (β)
- **Sign (+ / −)** → Direction of relationship  
- **Magnitude** → Strength of effect  

**Example:**
> β₁ = 0.8 → A 1-unit increase in NDVI increases mangrove density by **0.8 units**

---

### 🔹 Intercept (β₀)
- Expected value of Y when X = 0  
- Sometimes **not physically meaningful**, but required mathematically  

---

## 🔷 7. Evaluation Metrics

### 📌 R² (Coefficient of Determination)
\[
R^2 = 1 - \frac{RSS}{TSS}
\]

- Measures **variance explained by the model**
- Ranges from **0 to 1**

---

### 📌 Adjusted R²
- Penalizes unnecessary predictors  
- Preferred for **multiple regression**

---

### 📌 RMSE / MAE
- Measures **prediction error**
- Lower values indicate better performance  

---

## 🔷 8. Residual Analysis (Model Diagnostics)

**Residuals:**
\[
\text{Residual} = y - \hat{y}
\]

### Diagnostic Checks:
- **Residual vs Fitted Plot** → Linearity & homoscedasticity  
- **Q-Q Plot** → Normality  
- **Durbin–Watson Test** → Autocorrelation  
- **VIF (Variance Inflation Factor)** → Multicollinearity  

---

## 🔷 11. Strengths

✔ Simple and interpretable  
✔ Strong statistical foundation  
✔ Fast and computationally efficient  
✔ Performs well when assumptions hold  

---

## 🔷 12. Limitations

❌ Cannot capture non-linear relationships  
❌ Highly sensitive to outliers  
❌ Multicollinearity destabilizes coefficients  
❌ Assumptions often violated in real-world data  

---

