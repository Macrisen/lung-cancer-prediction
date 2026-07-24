# Lung Cancer Prediction — Statistics Group Project

**International University – Vietnam National University HCMC**
Group Project | Statistics Report | Semester 1, 2025–2026
Lecturer: Assoc. Prof. Dr. Nguyen Minh Quan

## 👥 Team members

| Name | Student ID | Contribution |
|---|---|---|
| Nguyen Truong Vy | MAMAIU23071 | Report, visualization, research data, presentation |
| Tran Thanh Son | MAMAIU23071 | Double-check data, visualization, double test, report |
| Truong Gia Kiet | MAMAIU23031 | Report, presentation |
| Pham Le Yen Nhi | MAMAIU22127 | Report, presentation |
| Dang Khanh Huyen | MAMAIU22066 | Slides, presentation |

## 📌 Overview

This project applies statistical and machine learning techniques to predict the probability of a person developing **lung cancer** based on demographic, behavioral, symptom, and biological data. The dataset (309 observations) is based on a Kaggle lung cancer survey, enriched with additional clinical biomarkers (FEV1, FVC, CRP, SpO₂).

**Research questions:**
- Which are the most influential lung cancer risk factors?
- Can a logistic regression model be used to predict lung cancer accurately?

## 🧰 Tools & libraries

- **pandas, NumPy** – data cleaning, processing, transformation
- **Matplotlib, Seaborn** – visualization (histograms, countplots, density plots, heatmaps)
- **scikit-learn** – `LogisticRegression`, `accuracy_score`, `classification_report`, `confusion_matrix`

## 🧪 Methodology

1. **Model:** Logistic Regression (chosen over linear regression since the outcome is binary: has lung cancer / does not).
2. **Descriptive statistics:** distributions, count plots, density plots, histograms, pairplots, correlation heatmap, boxplots for all variables stratified by lung cancer status.
3. **Inferential statistics:**
   - 90.3% confidence intervals for regression coefficients (MLE-based).
   - Two-sample t-tests for continuous variables (Smoking Years, CRP, FEV1, FVC, SpO₂, Age).
   - Chi-square test of independence (Smoking vs. Lung Cancer).
   - Train/test split (80/20, n=62 test) for model evaluation.

## 📊 Key findings

| Variable | Effect | Odds Ratio (approx.) | Significant? |
|---|---|---|---|
| Smoking Years | ↑ risk | 1.30 per year | ✅ Yes (strongest predictor) |
| CRP | ↑ risk | 2.12 per mg/L | ✅ Yes |
| FEV1 | ↓ risk as it rises | 0.94 | ✅ Yes |
| FVC | ↓ risk as it rises | 0.32 | ✅ Yes |
| SpO₂ | ↓ risk as it rises | 0.64 | ✅ Yes |
| Age | Negligible | 0.98 | ❌ No (p = 0.625) |
| Symptoms (cough, wheezing, fatigue, yellow fingers, chronic disease) | Weak/no effect | — | ❌ Mostly not significant |

- **Chi-square test:** strong association between smoking and lung cancer (χ² = 167.71, p < 0.0001).
- **Model performance:** ~90% test accuracy, AUC ≈ 0.90, recall (sensitivity) for cancer cases ≈ 0.94 — low false negatives, which is valuable for screening use cases.
- No serious multicollinearity among predictors (all |r| < 0.5).

## 💬 Discussion

Results align with established medical literature: long-term smoking drives lung cancer risk both directly and via chronic inflammation (elevated CRP) and declining lung function (FEV1, FVC, SpO₂). Interestingly, commonly assumed symptom indicators (coughing, wheezing, fatigue, yellow fingers) were **not** strong predictors — possibly because they appear late-stage, are self-reported (recall bias), or are already captured by the more objective biomarkers.

**Limitations:**
- Small sample size (n = 309), may limit generalizability.
- Kaggle survey data subject to selection bias (higher proportion of smokers/cancer cases than general population).
- Observational design — no causal inference; unmeasured confounders (genetics, occupational exposure, pollution, family history) not captured.

## ✅ Conclusion

The logistic regression model, using easily obtainable inputs (smoking history, CRP blood test, spirometry), can support personalized lung cancer risk estimation for early screening in primary care or occupational health settings. Smoking cessation remains the single most effective preventive measure. Future work could incorporate larger/more diverse datasets, genetic/environmental variables, more advanced ML models (Random Forest, Gradient Boosting), and external validation.

## 📁 Report structure

- Abstract
- I. Introduction
- II. Methodology (tools, model, descriptive & inferential statistics)
- III. Interpretation, Discussion, and Conclusion
- IV. References
- V. Appendices (dataset description, Python code, additional figures, team evaluation)

## 📚 References

- Al Aswad, N. (2020). *Lung cancer survey dataset* [Data set]. Kaggle.
- Hosmer, D. W., Lemeshow, S., & Sturdivant, R. X. (2013). *Applied Logistic Regression* (3rd ed.). Wiley.
- James, G., Witten, D., Hastie, T., & Tibshirani, R. (2021). *An Introduction to Statistical Learning: With Applications in R* (2nd ed.). Springer.
- Pedregosa, F., et al. (2011). Scikit-learn: Machine learning in Python. *JMLR*, 12, 2825–2830.
