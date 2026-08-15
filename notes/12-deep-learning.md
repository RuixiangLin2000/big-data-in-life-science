# 用于显微成像的深度学习（Deep Learning for Microscopy）

## 中文导读（Chinese Guide）

神经网络通过学习权重和偏置完成预测。训练包含前向传播、损失计算、反向传播和参数更新。训练性能不断提高而验证性能停滞或下降通常表示过拟合。

Dropout、权重衰减、数据增强、早停和减小模型规模可改善泛化。CNN 使用卷积滤波器提取空间模式；迁移学习复用预训练表示；残差连接改善深层网络的梯度传播；U-Net 适合图像分割；GAN 通过生成器与判别器对抗训练。

显微图像必须按独立实验单位划分，不能让同一孔或同一患者的相关图像跨越训练和验证集合。还应检查批次混杂、类别不平衡、独立生物重复不足和合成图像误用。

---

## 英文原文（Original English）

# Deep Learning for Microscopy

## Foundations

A neural network learns weights and biases. Each unit computes a weighted sum and applies a nonlinear activation such as sigmoid, tanh, or ReLU.

Training performs forward propagation, computes a loss, uses backpropagation to calculate gradients, and updates parameters with an optimizer. A widening training-validation gap indicates overfitting.

## Regularization

Dropout disables random units during training. Weight decay, data augmentation, early stopping, and smaller architectures can also improve generalization.

## CNN concepts

Convolutional neural networks exploit spatial structure with learned filters, activations, downsampling, and prediction heads. Early filters capture local patterns; later layers combine them into task-relevant representations.

## Architectures

- Transfer learning initializes from a pretrained network and fine-tunes it.
- Residual connections provide shorter gradient paths for deep networks.
- U-Net combines an encoder and decoder with skip connections for segmentation.
- Generative adversarial networks train a generator against a discriminator.

## Microscopy practice

Split by independent experimental unit rather than by image crop. Normalize channels consistently, retain plate and batch metadata, use biologically plausible augmentation, evaluate per class and batch, and experimentally confirm findings.

Major risks include leakage among images from one well, acquisition confounding, too few biological replicates, class imbalance, and treating synthetic images as verified observations.
