
# Bank Marketing Campaign – Model Evaluation Summary

## 📘 Objective
The goal of this project was to develop predictive models to identify clients most likely to subscribe to a long-term bank deposit using the **Bank Marketing Dataset**.  
We compared multiple classification algorithms using encoded customer data (demographics, financial info, campaign attributes).

---

## ⚙️ Models Evaluated
| Model | Train Accuracy | Test Accuracy | ROC-AUC | Training Time (s) | Key Insights |
|--------|----------------|----------------|----------|-------------------|---------------|
| **Dummy (Most Frequent)** | 0.887 | 0.887 | 0.500 | 0.02 | Baseline, no predictive skill |
| **Logistic Regression** | 0.904 | 0.905 | **0.876** | 1.04 | Best overall balance of performance and speed |
| **Decision Tree (max_depth=5)** | 0.909 | 0.906 | 0.855 | 0.07 | Interpretable, strong alternative |
| **SVM (RBF)** | 0.897 | 0.898 | 0.854 | 61.41 | Good accuracy but computationally expensive |
| **KNN (k=5)** | 0.999 | 0.884 | 0.780 | 0.04 | Overfits, weak generalization |
| **KNN (k=3)** | 0.999 | 0.879 | 0.746 | 0.03 | Overfitting, lower AUC |
| **KNN (k=7)** | 0.999 | 0.879 | 0.746 | 0.03 | Same pattern, no improvement |

---

## 🧩 Key Findings

1. **Logistic Regression** provides the **highest ROC-AUC (0.876)** and excellent generalization — minimal train/test gap.  
2. **Decision Tree (max_depth=5)** also performs well (AUC 0.855) and offers interpretability.  
3. **KNN** models exhibit **severe overfitting**, memorizing training data and failing to generalize.  
4. **SVM (RBF)** achieves comparable accuracy but at a much higher computational cost (61 seconds vs <1s for others).  
5. **Dummy Classifier** serves as a baseline benchmark — all other models outperform it.

---

## ⚖️ Generalization and Overfitting
- **Best generalizer:** Logistic Regression  
- **Controlled overfitting:** Decision Tree (depth 5)  
- **Severe overfitting:** KNN (any k)  
- **High compute time:** SVM (RBF)

---

## 🎯 Recommendations
- **Primary model:** Logistic Regression (efficient, accurate, generalizes well).  
- **For interpretability:** Decision Tree (max_depth=5).  
- **Avoid:** KNN (unstable) and SVM (too slow).  
- Consider **class weighting or resampling** to improve recall for minority “yes” class.  
- Future enhancements: test ensemble methods like **Random Forest** or **XGBoost**.

---

## 📈 Next Steps
1. Perform **hyperparameter tuning** on Decision Tree and Logistic Regression.  
2. Use **cross-validation** for robust performance estimation.  
3. Plot **ROC curves** for visual comparison.  
4. Deploy the best-performing model (Logistic Regression) into production workflow for campaign optimization.

---

*Prepared using Python (pandas, scikit-learn, matplotlib) in JupyterLab environment.*
