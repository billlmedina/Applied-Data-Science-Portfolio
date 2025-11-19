#  Taiwan Real Estate Price Prediction using Regularized Regression

This project implements a complete Machine Learning pipeline to predict house prices per unit area in Taiwan. Using **Ridge Regression ($\mathbf{L2}$)**, this analysis focuses on identifying the primary drivers of real estate value while employing regularization to build a stable and reliable predictive model.

---
###  Key Goals

1.  **Preprocessing & EDA:** Clean and scale data, and analyze feature correlations (e.g., distance to MRT, number of convenience stores).
2.  **Model Optimization:** Implement **Grid Search** and **Cross-Validation** to tune the regularization strength ($\alpha$) for the Ridge model.
3.  **Model Justification:** Compare Ridge Regression against OLS and Lasso to prove the stability benefits of regularization.
   
###  Methodology

The final model was selected based on optimal performance metrics across a comparative suite:

* **Model Used:** Ridge Regression ($\mathbf{L2}$ Regularization)
* **Tuning Method:** $\mathbf{GridSearchCV}$ to find the optimal $\mathbf{\alpha}$ (Regularization Strength).
* **Preprocessing:** $\mathbf{StandardScaler}$ was applied to all features to ensure equal contribution to the penalty term.

###  Data Source

The analysis uses the Taiwan Real Estate Valuation Data set, focusing on four key features:

| Feature | Description | Correlation with Price |
| :--- | :--- | :--- |
| $\mathbf{X3}$ Distance to the Nearest MRT Station | Meters to the nearest rapid transit. | Strong Negative ($\mathbf{-0.67}$) |
| $\mathbf{X4}$ Number of Convenience Stores | Count of stores in the locality. | Moderate Positive ($\mathbf{+0.57}$) |
| $\mathbf{X5/X6}$ Latitude/Longitude | Geographic coordinates. | Moderate Positive |

###  Final Results & Model Justification

#### 1. Performance Metrics

Ridge Regression outperformed the other linear models, demonstrating strong stability:

| Metric | Score | Justification |
| :--- | :--- | :--- |
| **R-squared ($\mathbf{R^2}$)** | **0.6209** | Model explains $\mathbf{62.1\%}$ of the variance in house prices. |
| **Mean Absolute Error (MAE)** | **6.2090** | Average prediction error is limited to $\mathbf{6.21}$ units (NT$/ping$). |

#### 2. Feature Importance

The model successfully quantified the impact of local amenities. The signs align perfectly with intuition:

* **Strongest Negative Driver:** $\mathbf{X3}$ Distance to MRT ($\mathbf{-5.42}$ standardized coefficient).
* **Primary Positive Drivers:** $\mathbf{X4}$ Convenience Stores ($\mathbf{+3.00}$) and $\mathbf{X5}$ Latitude ($\mathbf{+2.79}$).



**Model Justification:** The slight increase in $\mathbf{R^2}$ over OLS (0.6209 vs. 0.6191) combined with the stability provided by $\mathbf{L2}$ regularization made Ridge the optimal choice. It ensures the model is robust and not over-reliant on any single, potentially noisy feature.
