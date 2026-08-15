# Large-Scale Machine Learning

## Tasks

Supervised learning predicts labels or values from examples. Classification outputs categories; regression outputs numbers. Unsupervised learning seeks structure without target labels.

## Evaluation

Classification uses true/false positives and negatives. Accuracy is unreliable for rare outcomes. Precision measures how many positive predictions are correct; recall measures how many real positives are found; specificity measures rejection of negatives; F1 balances precision and recall; ROC-AUC summarizes ranking across thresholds.

Regression commonly uses RMSE and R-squared, but residual plots are needed to reveal systematic errors.

## Generalization

Overfitting means learning training-specific artifacts. Keep a final test set isolated from model choice. Cross-validation trains and validates across folds. Preprocessing, feature selection, and tuning must happen within each training fold to prevent leakage.

## Scaling

Use vectorized and sparse implementations, partition data, parallelize independent runs, distribute parameter searches, use suitable accelerators, and reduce feature or model complexity when justified. Monitor I/O because data movement may dominate compute time.

## Life-science validation

Samples may be grouped by patient, plate, batch, site, or chemical series. Random row-level splitting can leak group-specific signals. Design validation to match the intended future use and the different costs of false positives and false negatives.
