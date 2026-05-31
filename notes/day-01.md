# Day 1 — CIFAR-10 baseline

## What I built
I have built a simple 3 layer CNN, with no regularization, Adam lr=1e-3, 10 epochs and batch size 64. For training the input dataset(Tensor format of RGB images[CHW]) directly passed onto the convolution layer 1. In this layer the used filter size is 3 * 3 and input has 3 channels. The output of this layer is 32 different feature maps. For this this layer need 32 different filter for each channel. Thus number of learnable parameters of this layer is (3 * 3 * 3 * 32) 864. Then these 32 different feature maps pass through a pooling of 2 * 2. This makes the tensors 16*16 size. 
At layer 2 same process happens again but this time these pooled 32 feature maps are the input. The output of this layer is 64 different feature maps. Number of learnable parameter of this layer is (3 * 3 * 32 * 64) 18,432. The tensor height-width becomes 8*8. Similarly the number of learnable parameters at layer 3 is 73,728. After this layer the output is 128 different 4 * 4 feature maps. After this stage these feature maps are linearize and weighted to get 512 output neuron. Number of learning parameter this stage (128 * 4 * 4 * 256) 524,288. The next stage is same and learning parameters is 2560.
## About Dataset
The dataset i used is the built in dataset of torchvision library labeled CIFAR10. This dataset contains 60000 images and has 10 classes. Using the features of torchvision library i have loaded the train and test datasets.

## Result
- Final train acc: 94.46%
- Final test acc:  75.28%
- Best test acc:   75.78% at epoch 8

## Observation
Train or test gap widens from 0% at epoch 2 to 19% at epoch 10. Test acc plateaus
around epoch 7. Model overfits.

## What I didn't fully understand
- The pattern detecting at each stage that are represented with numbers. But the value is not actually tells anything about pattern that is getting detected

## Time spent
- 6-7hours
