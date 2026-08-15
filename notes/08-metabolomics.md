# 代谢组学与大数据（Metabolomics and Big Data）

代谢组学研究受遗传、生理、环境、饮食、药物和微生物组影响的小分子。（Metabolomics studies small molecules influenced by genetics, physiology, environment, diet, medication, and the microbiome.）

## 平台与研究类型（Platforms and study types）

质谱提供灵敏、高通量的测量，通常与色谱联用；核磁共振提供互补的结构信息。靶向研究定量预先定义的化合物，非靶向研究检测广泛特征，但鉴定困难。（Mass spectrometry provides sensitive high-throughput measurements, often after chromatographic separation. Nuclear magnetic resonance provides complementary structural information. Targeted studies quantify defined compounds; untargeted studies detect broad feature spaces but face a difficult identification problem.）

## 典型流程（Typical workflow）

1. 设计实验并随机化运行顺序。（Design the experiment and randomize run order.）
2. 准备样本并采集仪器数据。（Prepare samples and acquire instrument data.）
3. 检测并解析峰。（Detect and deconvolve peaks.）
4. 跨样本对齐特征。（Align features across samples.）
5. 过滤空白并进行质量控制。（Filter blanks and apply quality control.）
6. 校正漂移与批次效应。（Correct drift and batch effects.）
7. 归一化并转换。（Normalize and transform.）
8. 进行统计建模。（Perform statistical modeling.）
9. 注释或鉴定代谢物。（Annotate or identify metabolites.）
10. 解释通路并验证发现。（Interpret pathways and validate findings.）

## 核心挑战（Core challenges）

一个代谢物可能产生多个加合物、同位素和碎片；保留时间与强度会漂移；缺失值通常不是随机的；仪器批次可能压过生物信号，且许多特征仍无法鉴定。（One metabolite may create several adducts, isotopes, and fragments. Retention time and intensity drift. Missing values are often non-random. Instrument batches can dominate biology, and many features remain unidentified.）

应使用混合质控、空白、内标、随机进样顺序和明确的接受标准；准确质量匹配不等同于化学身份确认。（Use pooled controls, blanks, internal standards, randomized injection order, and explicit acceptance criteria. Distinguish accurate-mass matches from confirmed identities.）

保留原始数据、工作流参数、数据库版本和注释置信度。（Preserve raw data, workflow parameters, library versions, and annotation confidence.）
