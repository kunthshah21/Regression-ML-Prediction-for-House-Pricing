# Housing Price Prediction

---

## 1. Problem Statement
Accurately predicting housing prices is crucial in real estate, urban planning, and financial sectors. This model helps stakeholders (e.g., agencies, homebuyers, investors) make data-driven decisions regarding property investments, pricing strategies, and market trend analysis.

---

## 2. Proposed Solution
We compare multiple **machine learning regression algorithms** to estimate housing prices using features like property attributes, location, and more. The goal is:
- **Identify** the most effective model for housing price prediction.
- **Evaluate** models based on accuracy (Mean Squared Error) and explanatory power (R²).
- **Provide** insights for improving property valuation and market transparency.

---

## 3. Exploratory Data Analysis

### 3.1 Understanding the Data
- **Source:** [Kaggle House Prices – Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/data)  
- **Features:** 75 total, ~1500 instances.  
- **Challenge:** Fewer instances make thorough EDA essential.

### 3.2 Data Cleaning and Feature Reduction
- **Null Value Handling:**  
  - Numeric: Replaced nulls with the **mean** of each feature.  
  - Categorical: Replaced nulls with the **mode** of each feature.  
  - Features with >50% null values were **removed** altogether.

#### 3.2.1 Feature Encoding
- **One-Hot Encoding** performed on categorical variables.  
- Resulted in **217 columns** due to many categories.

#### 3.2.2 Feature Engineering
- **Principal Component Analysis (PCA)** to reduce dimensionality from 217 to 70 components.  
- Data was **scaled** (mean=0, std=1) before PCA.  
- Chose the number of components that explained ~70% of the variance.

---

## 4. Supervised Models Evaluation and Interpretation

### 4.1 Building Models
1. **Data Scaling:** Standard scaler for all numeric features.  
2. **Train-Test Split:** 80:20 ratio.  
3. **Cross-Validation & Grid Search:**  
   - Used **5-fold cross-validation**.  
   - Grid search for hyperparameter tuning.  
4. **Model Evaluation:** Mean Squared Error (MSE) and R².

### 4.2 Comparative Analysis and Model Selection

#### 4.2.1 Comparison of All Models

| Model            | Mean Squared Error (MSE) | R² Score |
|------------------|--------------------------:|---------:|
| **Decision Tree** |              1.52e+09     |     0.80 |
| **Linear Regression** |       1.19e+09     |     0.85 |
| **KNN**          |              7.97e+08     |     0.74 |
| **Random Forest** |       1.31e+09     |     0.83 |

- **Decision Tree**:  
  - R² = 0.80, MSE = 1.52e+09  
  - Captures ~80% variance but high MSE indicates large prediction errors.

- **Linear Regression**:  
  - **Highest R² = 0.85**, MSE ≈ 1.19e+09  
  - Explains most variance; reasonably low error; easy to interpret.

- **K-Nearest Neighbors (KNN)**:  
  - **Lowest MSE = 7.97e+08**, R² = 0.74  
  - Great at minimizing average error but less variance explanation.

- **Random Forest**:  
  - R² = 0.83, MSE = 1.31e+09  
  - Balances complexity and accuracy but doesn’t outperform Linear Regression or KNN in their respective strengths.

**Selected Model: Linear Regression**  
- **Why?**  
  1. **High Explanatory Power**: Highest R² (0.85) among models.  
  2. **Competitive Accuracy**: Reasonably low MSE (~1.19e+09).  
  3. **Simplicity & Interpretability**: Stakeholders can easily understand model outputs.

---

## 4.2 K-Means Clustering
- **Optimal K**: Found to be 4, based on **Elbow Method** and **Silhouette Score**.  
- Each cluster represents different housing segments based on similarities in features.

---

## 5. Business Application

The chosen **Linear Regression** model is well-suited for predicting housing prices:
- **R² ~0.85** provides solid explanatory insights.  
- **MSE ~1.19e+09** implies the average squared error margin in real-world currency terms—still reasonable, but improvements may be needed for high-stakes pricing decisions.

### 5.1 Cluster Descriptions for Housing Prices Analysis
Using **K-Means Clustering (k=4)**, we identified distinct profiles:

1. **Cluster 0: "Vintage Essentials"**  
   - Homes from early-mid 20th century (~1360 sq. ft).  
   - Moderate features, smaller garages, functional basements.  
   - **Stakeholders**:  
     - **Realtors**: Market as affordable or starter homes.  
     - **Buyers**: Budget-friendly options in established neighborhoods.

2. **Cluster 1: "Modern Comforts"**  
   - Newer builds (~2000), larger living areas (~1770 sq. ft).  
   - High-quality construction, well-finished basements, suburban.  
   - **Stakeholders**:  
     - **Realtors**: Emphasize modern amenities.  
     - **Buyers**: Turnkey properties requiring minimal updates.

3. **Cluster 2: "Classic Fixer-Uppers"**  
   - Early 20th-century builds (~1915), smaller, dated interiors.  
   - Higher potential for **renovation** and **value-add projects**.  
   - **Stakeholders**:  
     - **Realtors**: Market as investment or restoration opportunities.  
     - **Buyers**: Entry-level pricing with improvement upside.

4. **Cluster 3: "Suburban Classics"**  
   - Mid-20th century builds (~1964), ~1350 sq. ft, larger lots (~11,680 sq. ft).  
   - Balanced traditional layouts with some modern updates.  
   - **Stakeholders**:  
     - **Realtors**: Family-friendly suburban homes with moderate pricing.  
     - **Buyers**: Good space without major renovation needs.

---

## 5.2 Model Limitations
- **Feature Reduction with PCA**: While PCA improved model simplicity, it reduces direct interpretability of which original features drive predictions.  
- **Linear Regression Assumptions**: May not capture non-linear relationships well.  
- **Small Dataset**: With only ~1500 instances, model generalizability could be limited.

