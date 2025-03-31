# Linear Regression Model Analysis

This project involves the development and evaluation of a linear regression model to predict salaries (`salary_in_usd`). The analysis includes data preprocessing, model fitting, assumption checks, and diagnostic tests to ensure the validity of the regression model.

---

## **1. Data Preprocessing**
- **Log Transformation**:
  - Applied log transformation to the target variable (`salary_in_usd`) to stabilize variance and improve normality.
- **Box-Cox Transformation**:
  - Applied Box-Cox transformation to further stabilize variance and improve normality when the target variable is positive.

---

## **2. Model Fitting**
- **Ordinary Least Squares (OLS)**:
  - Fitted a linear regression model using `statsmodels` with the transformed target variable.
  - Key metrics:
    - **R-squared**: Proportion of variance explained by the model.
    - **Adjusted R-squared**: Adjusted for the number of predictors.
    - **F-statistic**: Tests the overall significance of the model.
    - **P-values for coefficients**: Tests the significance of individual predictors.

---

## **3. Diagnostic Tests**
### **a. Shapiro-Wilk Test (Normality of Residuals)**
- **Purpose**: Tests whether the residuals are normally distributed.
- **Results**:
  - Log Transformation: `W = 0.9047, p-value = 0.0000`
  - Box-Cox Transformation: Improved normality slightly but residuals are still not fully normal.
- **Conclusion**: Residuals deviate from normality. Consider additional transformations or robust regression techniques.

### **b. Breusch-Pagan Test (Homoscedasticity)**
- **Purpose**: Tests for constant variance of residuals (homoscedasticity).
- **Results**:
  - Log Transformation: `p-value = 0.0000`
  - Box-Cox Transformation: Heteroscedasticity persists.
- **Conclusion**: Residuals exhibit heteroscedasticity. Use robust standard errors or weighted least squares (WLS).

### **c. Durbin-Watson Test (Autocorrelation)**
- **Purpose**: Tests for autocorrelation in residuals.
- **Results**:
  - Log Transformation: `Durbin-Watson = 1.5182`
  - Box-Cox Transformation: Autocorrelation persists.
- **Conclusion**: Positive autocorrelation is present. Investigate time-series effects or use generalized least squares (GLS).

---

## **4. Diagnostic Plots**
### **a. Q-Q Plot (Normality Check)**
- **Observation**: Residuals deviate from the straight line, especially at the tails.
- **Conclusion**: Residuals are not normally distributed.

### **b. Residuals vs. Fitted Values (Homoscedasticity Check)**
- **Observation**: Residuals show a clear pattern and fan out as fitted values increase.
- **Conclusion**: Heteroscedasticity is present.

### **c. Scale-Location Plot (Linearity Check)**
- **Observation**: √|Residuals| increase with fitted values, showing a clear pattern.
- **Conclusion**: Non-linearity and heteroscedasticity are present.

### **d. Histogram of Residuals**
- **Observation**: Residuals are skewed and not centered around zero.
- **Conclusion**: Residuals are not normally distributed.

---

## **5. Recommendations**
1. **Address Normality**:
   - Explore additional transformations (e.g., Box-Cox, Yeo-Johnson).
   - Use non-parametric regression techniques if normality is critical.
2. **Address Heteroscedasticity**:
   - Use robust standard errors (e.g., `HC3`) or weighted least squares (WLS).
3. **Address Autocorrelation**:
   - Investigate time-series effects and consider adding lagged variables.
   - Use GLS regression if autocorrelation persists.
4. **Refine the Model**:
   - Remove non-significant predictors to simplify the model.
   - Consider adding interaction terms or polynomial terms for non-linear relationships.

---

## **6. Key Learnings**
- Transformations like log and Box-Cox can improve model assumptions but may not fully resolve issues.
- Diagnostic tests and plots are essential for validating regression assumptions.
- Robust regression techniques and alternative models (e.g., GLS, WLS) can address violations of assumptions.

---

## **7. Tools and Libraries**
- **Python Libraries**:
  - `pandas`, `numpy`: Data manipulation and numerical computations.
  - `statsmodels`: Regression modeling and diagnostic tests.
  - `scipy`: Statistical transformations and tests.
  - `matplotlib`, `seaborn`: Data visualization.
- **Key Functions**:
  - `boxcox`: Box-Cox transformation.
  - `shapiro`: Shapiro-Wilk test for normality.
  - `het_breuschpagan`: Breusch-Pagan test for heteroscedasticity.
  - `durbin_watson`: Durbin-Watson test for autocorrelation.

---

## **8. Future Work**
- Explore advanced regression techniques (e.g., Ridge, Lasso, ElasticNet).
- Investigate feature engineering to improve model performance.
- Evaluate alternative models (e.g., decision trees, random forests) for better handling of non-linear relationships.