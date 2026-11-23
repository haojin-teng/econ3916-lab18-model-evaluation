# Model Evaluation: The Curve, and What It Cannot Tell You

## Objective
I compared two classifiers on a rare outcome and chose a threshold using error costs.

## Methodology
- Simulated 8,000 cases; 11.8% of test rows were positive
- Drew ROC and precision-recall curves for a logistic regression
- Compared it with a boosted-tree model using a paired bootstrap (500 resamples)
- Chose the cheapest threshold at a 10:1 cost ratio on the training rows and priced it on the test rows
- Wrote roc_point() to get one point on the ROC curve

## Key Findings
- Logistic: ROC AUC 0.847, AP 0.465. Boosted: ROC AUC 0.8431
- AUC difference +0.0038, 95% interval [−0.0020, +0.0094]: the models cannot be ranked
- Threshold 0.0905 cost 0.4692 per case, vs 0.9437 at 0.5
- At 0.0905: FPR 0.296, TPR 0.823
