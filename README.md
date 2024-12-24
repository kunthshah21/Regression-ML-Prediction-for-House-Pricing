# Machine Learning Model Performance and Insights

This project aimed to use multiple supervised and unsupervised machine learning algorithms to find the best-performing model for this dataset. This involved thorough EDA with the help of fixing null values with mean and mode. Performing multi-class analysis and correlation analysis. Lastly, PCA was applied for feature engineering. The exact implementation is provided in the report. 

The data was also scaled using `StandardScaler`, and the models were tested and iterated with proper hyperparameter tuning with a 5-fold cross-validation.

---

## Supervised Machine Learning Models

### Summary of Model Performance

| Model                      | Mean Squared Error (MSE) | R² Score |
|----------------------------|--------------------------|----------|
| Decision Tree              | 1.52e+09                | 0.80     |
| Linear Regression          | 1.19e+09                | 0.85     |
| K-Nearest Neighbors (KNN)  | 7.97e+08                | 0.74     |
| Random Forest              | 1.31e+09                | 0.83     |

### Model Selection

Given the metrics, **Linear Regression** is the best choice. Its combination of the highest R² score (0.85) and a low MSE (~1.19e+09) ensures that it captures substantial variance in the target while maintaining accurate predictions.

**Rationale:**
1. **High Explanatory Power:** Linear Regression’s R² (0.85) outperforms all other models, providing the clearest understanding of how features influence the target.
2. **Reliable Accuracy:** Its low MSE (~1.19e+09) ensures that predictions closely match actual values, reducing costly misjudgments.
3. **Simplicity and Interpretability:** The straightforward nature of Linear Regression makes it easy to understand and deploy.

---

## Unsupervised Machine Learning Models

### K-Means Clustering

- **Optimal Number of Clusters (k):** 4  
- The K-Means model was chosen to cluster features and derive potential business insights.  
- Detailed business insights from clustering analysis are provided in the report.
