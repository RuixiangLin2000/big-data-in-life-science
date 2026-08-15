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
