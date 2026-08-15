# 用于显微成像的深度学习（Deep Learning for Microscopy）

## 基础（Foundations）

神经网络学习权重和偏置，每个单元计算加权和并应用 sigmoid、tanh 或 ReLU 等非线性激活函数。（A neural network learns weights and biases. Each unit computes a weighted sum and applies a nonlinear activation such as sigmoid, tanh, or ReLU.）

训练包括前向传播、损失计算、反向传播和优化器更新参数。训练与验证性能的差距持续扩大通常表示过拟合。（Training performs forward propagation, computes a loss, uses backpropagation to calculate gradients, and updates parameters with an optimizer. A widening training-validation gap indicates overfitting.）

## 正则化（Regularization）

Dropout 在训练时随机停用单元；权重衰减、数据增强、早停和更小的网络也能改善泛化。（Dropout disables random units during training. Weight decay, data augmentation, early stopping, and smaller architectures can also improve generalization.）

## CNN 概念（CNN concepts）

卷积神经网络通过学习到的滤波器、激活、下采样和预测头利用空间结构。浅层滤波器常捕获局部模式，深层组合出任务相关表示。（Convolutional neural networks exploit spatial structure with learned filters, activations, downsampling, and prediction heads. Early filters capture local patterns; later layers combine them into task-relevant representations.）

## 架构（Architectures）

- 迁移学习从预训练网络初始化并针对新任务微调。（Transfer learning initializes from a pretrained network and fine-tunes it.）
- 残差连接为深层网络提供更短的梯度路径。（Residual connections provide shorter gradient paths for deep networks.）
- U-Net 使用带跳跃连接的编码器—解码器进行分割。（U-Net combines an encoder and decoder with skip connections for segmentation.）
- GAN 让生成器与判别器竞争以学习数据分布。（Generative adversarial networks train a generator against a discriminator.）

## 显微成像实践（Microscopy practice）

应按独立实验单位而不是图像裁剪划分数据，统一归一化通道，保留孔板和批次元数据，使用生物学合理的数据增强，按类别和批次评估，并通过实验确认发现。（Split data by independent experimental unit rather than by image crop. Normalize channels consistently, retain plate and batch metadata, use biologically plausible augmentation, evaluate per class and batch, and experimentally confirm findings.）

主要风险包括同一孔图像之间的泄漏、采集批次混杂、生物学独立样本过少、类别不平衡，以及把合成图像当作已验证的生物观测。（Major risks include leakage among images from one well, acquisition confounding, too few biological replicates, class imbalance, and treating synthetic images as verified observations.）
