# 作业 3：用于显微成像的深度学习（Assignment 3: Deep Learning for Microscopy）

## 中文导读（Chinese Guide）

目标是建立显微图像分类器，并通过连续实验说明模型与数据决策如何影响平衡准确率、可靠性和临床解释。

要求包括一个有意受限的低性能模型、一个逐步改进并达到目标表现的模型，以及至少两次从当前最新模型继续进行的明确修改。报告需列出训练、验证和测试结果、分类别表现、其他合理指标、每次改变的理由，以及最终模型的局限性。

应重点讨论患者级数据泄漏、类别不平衡、染色和成像变化、随机性与过拟合。Notebook 必须从头成功运行，路径应可移植或有说明。公开页面不包含学生模型代码、答案、姓名或小组结果。

---

## 英文原文（Original English）

# Assignment 3: Deep Learning for Microscopy

## Goal

Develop a microscopy image classifier while demonstrating how model and data decisions affect balanced accuracy, reliability, and clinical interpretation.

## Required experimental progression

The supplied instructions require:

1. An intentionally limited model with validation balanced accuracy below 65%.
2. A model-development sequence that reaches at least 82% validation balanced accuracy.
3. At least two clearly documented changes made sequentially from the latest model.
4. A final report of training, validation, and test performance.
5. Per-class performance and answers to the required reflection questions.

The educational goal is not only reaching a threshold; it is explaining what changed, why it changed, and whether it helped.

## Report structure

A compliant report should contain:

- Final balanced accuracy near the beginning
- Training, validation, and test results
- Per-class results
- Additional justified metrics
- Initial model and rationale
- Sequential model changes
- Evidence for each change
- Final-model evaluation
- Answers to all reflection questions
- Strengths, limitations, and clinical caution

## Metrics

Balanced accuracy is important when class sizes differ. Also consider:

- recall or sensitivity
- specificity
- precision
- F1 score
- confusion matrix
- variability across repeated runs

A clinical recommendation cannot be based on accuracy alone.

## Experimental design issues

Images from the same patient or experimental source must not silently leak across training and validation partitions. A patient-level split usually provides a more realistic, and often lower, estimate of generalization to unseen patients.

Other risks include staining differences, acquisition changes, population shift, class imbalance, nondeterminism, and overfitting.

## Notebook checklist

- [ ] Shut down unnecessary kernels to preserve GPU memory
- [ ] Use portable or clearly documented paths
- [ ] Fix and record random seeds where feasible
- [ ] Keep preprocessing consistent across splits
- [ ] Do not augment validation or test data
- [ ] Restart the kernel and run all cells successfully
- [ ] Remove personal paths and machine identifiers
- [ ] Export both required formats
- [ ] Follow the exact current naming and report rules

## 2026-specific administrative note

The supplied material lists attempt-counting milestones on 25 May and 14 June 2026, followed by an August re-examination opportunity. These dates are historical course metadata; confirm all deadlines and attempt rules on the official platform.

No student model code, completed answers, personal names, or achieved group results are published here.
