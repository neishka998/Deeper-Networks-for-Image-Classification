# Deeper Networks for Image Classification

## Introduction

Here, I experimented with three of the most well-known deep networks: 
* VGG (VGG16, VGG19),
* GoogleNet, 
* ResNet (ResNet18, ResNet34)

I tested different configurations of these networks using the *MNIST* and *CIFAR10* datasets, including batch size, learning rate, optimizer, data preprocessing, and augmentation. For each of these combinations, models were evaluated based loss, accuracy, convergence and time to train also comparing the performance of families of models and observing how factors such as data augmentation, network depth, and network blocks (inception block, residual block) affect model performance.


## Model Architectures 

### *1. VGG*

<img align="left" src="https://github.com/neishka998/Deeper-Networks-for-Image-Classification/blob/main/images/Screenshot%202021-05-26%20at%2012.44.13%20AM.png" alt="alt text" width="450" height="300">

The configurations VGG16 and VGG19 were used for VGG. The VGG16 network consists of 13 convolutional layers and fully connected layers. In the convolution layer, it uses 3 x 3 filters with a stride of 1 and uses same padding in pooling layers containing 2 x 2 filters with a stride of 2. VGG16 has a total of 138 million parameters.

An additional variant VGG19 has 19 weight layers, including 16 convolutional layers (with the same 5 pooling layers), 3 fully connected layers, and a softmax layer. The architecture consists of two Fully Connected layers with 4096 channels each which is followed by another fully connected layer with 1000 channels to predict 1000 labels.

From both variation of VGG, out of 3 fully connected convolutional layers, 2 of them have 4096 channels each whereas, the third layer just has 10 channels. Noting that the experiment uses both the CIFAR10 and the MNIST datasets, each of which has 10 classes. Hence, it is was imperative to modify the VGG network before the training to have 10 output channels. Earlier, VGGNet had 1000 output channels as it was trained on ImageNet Dataset.

ReLU activation function is used for all the hidden layers in the network.

### *2. GoogleNet*
<img align="left" src="https://github.com/neishka998/Deeper-Networks-for-Image-Classification/blob/main/images/Screenshot%202021-05-26%20at%2012.57.33%20AM.png" alt="alt text" width="450" height="300">

In this experiment, Inception Net V1 is used (GoogleNet). This architecture is made up of 22 layers and has a total of 9 inception modules (27 layers including pooling layers). With an Inception Module, multiple filter sizes can be used in a single image block, which is then concatenated and transferred to the next layer. It uses global average pooling at the end of the previous inception module. The final layer is a linear layer with 1000-unit softmax activation functions, which corresponds to the 1000 classes of ImageNet dataset. However, the experiment used datasets (CIFAR10 and MNIST) for only 10 classes, and the output channels in the network were modified to 10. A dropout layer (40%) is utilized just before the linear layer.

Additionally, an extra component that was implemented by the creators of the network to regularise and prevent overfitting and is known as an Auxiliary Classifier. Auxiliary Classifiers are applied to the architecture's intermediate layers. Auxiliary Classifiers are only used for training purposes. Their goal is to conduct a classification based on the inputs within the network's midsection and then add the loss measured during training to the network's total loss. This model has about 5 million parameters.

