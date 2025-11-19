#  Applied-Data-Science-Portfolio

A focused portfolio showcasing **full-stack data science competency**, from EDA and Feature Engineering to advanced Statistical and Deep Learning Models. Core projects include **Time Series Forecasting (SARIMA)** for market prediction and **Regularized Regression (Ridge)** for real estate valuation.

---

##  Core Competencies Demonstrated

| Skill Category | Techniques Used | Project Application |
| :--- | :--- | :--- |
| **Predictive Modeling** | SARIMA, Ridge Regression, OLS, Lasso, Ensemble Methods | Price forecasting and real estate valuation. |
| **Model Optimization** | $\mathbf{L2}$ Regularization (Ridge), $\mathbf{GridSearchCV}$, Cross-Validation. | Fine-tuning model stability and preventing overfitting on complex data. |
| **Time Series Analysis** | ADF Testing, ACF/PACF plots, Seasonal Differencing. | Capturing seasonality and trend volatility in market price data. |
| **Data Preparation** | Feature Scaling ($\mathbf{StandardScaler}$), Feature Selection, Correlation Analysis. | Preparing real-world datasets for consumption by penalty-based models. |

---

##  Project 1: Talipapa (Philippine Market Price Forecasting)

This project addresses market volatility by implementing a time series forecasting solution for Philippine agri-fishery commodities.

### Methodology

* **Model:** **SARIMA-Exponential Smoothing Ensemble** (70% SARIMA, 30% Holt-Winters).
* **Goal:** Forecast weekly average retail prices for the subsequent 2-4 weeks.
* **Tuning:** $\mathbf{pmdarima}$ was used to automatically tune the SARIMA parameters $\mathbf{(p, d, q) \times (P, D, Q, s)}$ based on AIC minimization.

### Performance

The ensemble approach yielded extremely high accuracy across commodities:

| Metric | Average Score | Interpretation |
| :--- | :--- | :--- |
| **Mean Absolute Error (MAE)** | **1.86** | Minimal absolute deviation from actual prices. |
| **Mean Absolute Percentage Error (MAPE)** | **1.43%** | An **exceptionally low error rate** (MAPE < 5% is considered excellent), validating the model's suitability for complex seasonal market data. |

---

##  Project 2: Taiwan Real Estate Price Predictor (Regression)

This project implements a complete Machine Learning pipeline to predict house prices in Taiwan, focusing on **optimized linear regression** to ensure stability and interpretability.

### Methodology

* **Model:** **Ridge Regression** ($\mathbf{L2}$ Regularization), selected via $\mathbf{GridSearchCV}$ to find the optimal regularization strength ($\alpha$).
* **Data Preparation:** Features scaled using $\mathbf{StandardScaler}$.
* **Key Features:** Distance to the nearest MRT station, number of convenience stores, and geographic coordinates (Latitude/Longitude).

### Model Justification (Comparative Analysis)

Ridge Regression was chosen because it achieved the best balance of accuracy and stability, outperforming OLS (Standard Linear Regression) and Lasso.

| Model | R² Score | MAE | RMSE | Justification |
| :--- | :--- | :--- | :--- | :--- |
| **Ridge Regression** | **0.6209** | **6.2090** | **7.9744** | **Optimal Model:** Provides stability and generalization against correlated location features. |
| Linear Regression (OLS) | 0.6191 | 6.2436 | 7.9941 | Lacks the generalization benefit of Ridge, making it unstable. |
| Lasso Regression | -0.0251 | 10.9167 | 13.1137 | Failed, as the L1 penalty eliminated critical features. |

### Interpretation: Feature Importance

The model successfully quantified the economic influence of local amenities. **MRT Distance** is the strongest price factor.

| Feature | Standardized Coefficient | Economic Interpretation |
| :--- | :--- | :--- |
| **X3 distance to the nearest MRT station** | **-5.4191** | **Strongest Negative Driver:** Closer proximity significantly increases price. |
| **X4 number of convenience stores** | **+3.0027** | **Strong Positive Driver:** Accessibility adds significant value. |


---


## 🛠️ Setup and Environment

To run these notebooks locally, clone the repository and install the required dependencies:

```bash
# Core Libraries for both projects
pip install pandas numpy scikit-learn matplotlib seaborn

# Specific libraries for Time Series (Talipapa)
pip install pmdarima statsmodels
