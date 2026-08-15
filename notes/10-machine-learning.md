# 大规模机器学习（Large-Scale Machine Learning）

## 中文导读（Chinese Guide）

监督学习从带标签数据预测类别或数值，非监督学习在没有目标标签时寻找结构。分类评估包括准确率、精确率、召回率、特异度、F1 和 ROC-AUC；类别极不平衡时，准确率可能产生误导。

过拟合表示模型学习了训练集特有的伪规律。最终测试集不能参与模型选择，交叉验证中的预处理、特征选择和调参必须在每个训练折内部完成。

大规模训练应使用向量化、稀疏实现、数据分区、独立任务并行和适当的硬件加速。生命科学数据常按患者、孔板、批次、中心或化学系列成组，随机按行划分可能产生严重泄漏。

---

## 英文原文（Original English）

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
