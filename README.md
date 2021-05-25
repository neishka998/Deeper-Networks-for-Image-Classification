# Deeper Networks for Image Classification

## Introduction

Here, I experimented with three of the most well-known deep networks: 
* VGG (VGG16, VGG19),
* GoogleNet, 
* ResNet (ResNet18, ResNet34)

I tested different configurations of these networks using the *MNIST* and *CIFAR10* datasets, including batch size, learning rate, optimizer, data preprocessing, and augmentation. For each of these combinations, models were evaluated based loss, accuracy, convergence and time to train also comparing the performance of families of models and observing how factors such as data augmentation, network depth, and network blocks (inception block, residual block) affect model performance.


## Model Architectures 

### *1. VGG*

The configurations VGG16 and VGG19 were used for VGG. The VGG16 network consists of 13 convolutional layers and fully connected layers. In the convolution layer, it uses 3 x 3 filters with a stride of 1 and uses same padding in pooling layers containing 2 x 2 filters with a stride of 2. VGG16 has a total of 138 million parameters.

An additional variant VGG19 has 19 weight layers, including 16 convolutional layers (with the same 5 pooling layers), 3 fully connected layers, and a softmax layer. The architecture consists of two Fully Connected layers with 4096 channels each which is followed by another fully connected layer with 1000 channels to predict 1000 labels.

From both variation of VGG, out of 3 fully connected convolutional layers, 2 of them have 4096 channels each whereas, the third layer just has 10 channels. Noting that the experiment uses both the CIFAR10 and the MNIST datasets, each of which has 10 classes. Hence, it is was imperative to modify the VGG network before the training to have 10 output channels. Earlier, VGGNet had 1000 output channels as it was trained on ImageNet Dataset.

ReLU activation function is used for all the hidden layers in the network.

The Experiment was conducted using various configurations of three deep network architectures, namely VGG, ResNet, and GoogleNet, in this paper. As observed, fine-tuning the hyperparameters and configurations affects the model's accuracy. Also, during experiment, data augmentation was done for training to add variety by adding random (but realistic) transformations like image rotation, image flip, and random crop. This ultimately helps in the generalisation of the model and the avoidance of overfitting. Bi-cubic Interpolation was used to resize both datasets to 64*64 pixels for data pre-processing. For MNIST dataset, which is grayscale, the dataset was converted to three channels.
