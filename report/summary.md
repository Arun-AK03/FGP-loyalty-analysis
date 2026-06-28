# FGP Loyalty Program — Analysis Summary

This is a written walkthrough of the analysis contained in the Excel workbook.

## 1. Preprocessing
- Recoded placeholder birth-year values (1 Jan 1900) and removed one implausible record.
- Dummy-coded gender, race, home city, car and credit-card ownership, and activity status.
- Derived `Age` from birth year.
- Final working set: 3,212 customers.

## 2. Active vs. churned (2019)
- 75.5% retained, 24.5% churned.
- Active customers skewed female, more likely to own a credit card, and concentrated in major cities; they also reported higher satisfaction and Net Promoter scores and higher 2018 spend.

## 3. Churn model (logistic regression)
- Target: active in 2019 (1) vs. churned (0).
- ~90% accuracy, AUC ≈ 0.90, McFadden R² ≈ 0.43.
- Positive predictors of retention: female, car owner, higher Sat_Program, higher NetPromoter.
- Higher churn risk: City D residents; more 2018 redemption activity.

## 4. Diagnostics
- Correlation matrix + VIF (all < 5) confirmed multicollinearity was not a concern.

## 5. CLV
- CLV = (1 + r) / (1 − p + r) × (R − C) − A, using 2018 revenue (R), redemption cost (C, 1 pt = $0.01), discount rate r = 10%, retention rate p, acquisition cost A = 0.

## 6. Segmentation (K-means)
- K = 3 (elbow method), silhouette ≈ 0.50, visualised with PCA.
- Stable (~72%), Enterprise (~1%), High-risk (~27%) — see README for profiles and strategies.

## Recommended figures to export from the workbook into /images
- Active vs. churned comparison chart
- Logistic regression results / classification table
- VIF table
- CLV distribution
- Elbow plot and PCA cluster scatter
