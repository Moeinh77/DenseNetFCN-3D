# DenseNet3D and DenseNet3D-FCN models for Keras.

Adapted DenseNet and DensetNet-FCN to work with 3D input for volume classification and segmentation.

DenseNet is a network architecture where each layer is directly connected
to every other layer in a feed-forward fashion (within each dense block).
For each layer, the feature maps of all preceding layers are treated as
separate inputs whereas its own feature maps are passed on as inputs to
all subsequent layers. This connectivity pattern yields state-of-the-art
accuracies on CIFAR10/100 (with or without data augmentation) and SVHN.
On the large scale ILSVRC 2012 (ImageNet) dataset, DenseNet achieves a
similar accuracy as ResNet, but using less than half the amount of
parameters and roughly half the number of FLOPs.

DenseNets can be extended to image segmentation tasks as described in the
paper "The One Hundred Layers Tiramisu: Fully Convolutional DenseNets for
Semantic Segmentation". Here, the dense blocks are arranged and concatenated
with long skip connections for state of the art performance on the CamVid dataset.

## Usage:
```python
!git clone 'http://github.com/GalDude33/DenseNetFCN-3D.git'
%cd DenseNetFCN-3D
!pip install git+https://www.github.com/keras-team/keras-contrib.git

from DenseNet3D import DenseNet3DImageNet121

model = DenseNet3DImageNet121(input_shape=(in_size, in_size, in_dim, 1),
                          bottleneck=True,
                          reduction=0.5,
                          dropout_rate=0.0,
                          weight_decay=1e-4,
                          include_top=True, # since i have no layer after this model
                          input_tensor=None,
                          pooling='avg',
                          classes=1,
                          activation='sigmoid')
```

## Reference
- [Densely Connected Convolutional Networks](https://arxiv.org/pdf/1608.06993.pdf)
- [The One Hundred Layers Tiramisu: Fully Convolutional DenseNets for Semantic
   Segmentation](https://arxiv.org/pdf/1611.09326.pdf)

This implementation is based on the following reference code:
 - https://github.com/gpleiss/efficient_densenet_pytorch
 - https://github.com/liuzhuang13/DenseNet
 - https://github.com/keras-team/keras-contrib/blob/master/keras_contrib/applications/densenet.py
 
 
