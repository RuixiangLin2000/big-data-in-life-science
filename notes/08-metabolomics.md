# 代谢组学与大数据（Metabolomics and Big Data）

## 中文导读（Chinese Guide）

代谢组学研究受遗传、生理、环境、饮食、药物和微生物组影响的小分子。质谱具有高灵敏度和高通量，核磁共振提供互补的结构信息。

标准流程包括实验设计、样本制备、峰检测、跨样本对齐、空白过滤、质量控制、漂移与批次校正、归一化、统计建模、代谢物注释和通路解释。

主要困难是一个代谢物可能产生多个加合物、同位素和碎片，保留时间和强度会漂移，缺失往往不是随机的，且大量特征无法被确定鉴定。应使用混合质控样本、空白、内标和明确的鉴定置信等级。

---

## 英文原文（Original English）

# Metabolomics and Big Data

Metabolomics studies small molecules influenced by genetics, physiology, environment, diet, medication, and the microbiome.

## Platforms and study types

Mass spectrometry provides sensitive high-throughput measurements, often after chromatographic separation. Nuclear magnetic resonance provides complementary structural information. Targeted studies quantify defined compounds; untargeted studies detect broad feature spaces but face a difficult identification problem.

## Typical workflow

1. Design the experiment and randomize run order.
2. Prepare samples and acquire instrument data.
3. Detect and deconvolve peaks.
4. Align features across samples.
5. Filter blanks and apply quality control.
6. Correct drift and batch effects.
7. Normalize and transform.
8. Perform statistical modeling.
9. Annotate or identify metabolites.
10. Interpret pathways and validate findings.

## Core challenges

One metabolite may create several adducts, isotopes, and fragments. Retention time and intensity drift. Missing values are often non-random. Instrument batches can dominate biology, and many features remain unidentified.

Use pooled controls, blanks, internal standards, randomized injection order, and explicit acceptance criteria. Distinguish accurate-mass matches from confirmed identities. Preserve raw data, workflow parameters, library versions, and annotation confidence.
