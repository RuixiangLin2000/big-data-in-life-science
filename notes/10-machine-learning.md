# 大规模机器学习（Large-Scale Machine Learning）

## 任务类型（Tasks）

监督学习从样本预测标签或数值；分类输出类别，回归输出数字；非监督学习在没有目标标签时寻找结构。（Supervised learning predicts labels or values from examples. Classification outputs categories; regression outputs numbers. Unsupervised learning seeks structure without target labels.）

## 评估（Evaluation）

分类结果包括真阳性、真阴性、假阳性和假阴性。稀有结局下准确率并不可靠。（Classification uses true/false positives and negatives. Accuracy is unreliable for rare outcomes.）

精确率衡量阳性预测中有多少正确；召回率衡量真实阳性中有多少被找到；特异度衡量阴性被排除的比例；F1 平衡精确率与召回率；ROC-AUC 概括不同阈值下的排序能力。（Precision measures how many positive predictions are correct; recall measures how many real positives are found; specificity measures rejection of negatives; F1 balances precision and recall; ROC-AUC summarizes ranking across thresholds.）

回归常使用 RMSE 和 R-squared，但仍需检查残差以发现系统性误差。（Regression commonly uses RMSE and R-squared, but residual plots are needed to reveal systematic errors.）

## 泛化（Generalization）

过拟合是学习训练集特有的伪规律。最终测试集必须与模型选择隔离；交叉验证中的预处理、特征选择和调参必须在每个训练折内部完成以防止泄漏。（Overfitting means learning training-specific artifacts. Keep a final test set isolated from model choice. Cross-validation trains and validates across folds. Preprocessing, feature selection, and tuning must happen within each training fold to prevent leakage.）

## 扩展（Scaling）

使用向量化和稀疏实现、数据分区、独立运行并行、分布式参数搜索、合适的加速器，以及有依据的特征或模型简化。还要监控 I/O，因为数据移动可能主导计算时间。（Use vectorized and sparse implementations, partition data, parallelize independent runs, distribute parameter searches, use suitable accelerators, and reduce feature or model complexity when justified. Monitor I/O because data movement may dominate compute time.）

## 生命科学验证（Life-science validation）

样本可能按患者、孔板、批次、中心或化学系列分组，随机按行划分可能泄漏组特异信号。验证设计应匹配未来用途，并反映假阳性与假阴性的不同代价。（Samples may be grouped by patient, plate, batch, site, or chemical series. Random row-level splitting can leak group-specific signals. Design validation to match the intended future use and the different costs of false positives and false negatives.）
