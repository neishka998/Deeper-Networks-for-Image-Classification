# Deeper Networks for Image Classification

Training Deeper Convolutional Neural Networks from scratch for Image Classification probelm on MNIST & CIFAR10. Models used are:
* VGG16 & VGG19
* GoogleNet
* ResNet


The Experiment was conducted using various configurations of three deep network architectures, namely VGG, ResNet, and GoogleNet, in this paper. As observed, fine-tuning the hyperparameters and configurations affects the model's accuracy. Also, during experiment, data augmentation was done for training to add variety by adding random (but realistic) transformations like image rotation, image flip, and random crop. This ultimately helps in the generalisation of the model and the avoidance of overfitting. Bicubicinterpolation was usedto resize both datasets to 64*64 pixels for data pre-processing. For MNIST dataset, which is grayscale, the dataset was converted to three channels.
