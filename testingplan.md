## Formal Testing Plan

In this blog, we will try to set up a formal plan for testing the capsule network inside out by using different methods. 

### Method 1: Testing by changing CPU/GPU
For this method, we we use CPU and GPU respectively to see if the accuracy of the capsule network is kept the same and the time of training neural work of GPU is shorter than that of CPU

### Method 2: Testing by changing the number of machines
This method is to test the distributed mechanism of neural network. Since we use Horovod, a distributed training framework for neural network, we will divide the training data to different batches, and we will send those batches to different machines to boost up the training time.
For this method, we will test it with 5 machines, 10 machines, and 15 machines

### Method 3: Testing by changing the epoch
Epoch is the time we execute one forward pass and one backward pass of all the training examples. 1 epoch means we will do 1 forward pass and one backward pass of all the training examples.
5 epochs mean we will do 5 forward pass and one backward pass of all the training examples. In the paper, Hinton et.al use 1250 epochs to train on MNIST dataset, which takes a lot of time. The implementation of the capsulenet that we are testing use 50 epochs. Since we can achieve around 97% accuracy with just 5 epochs for MNIST dataset, we will adjust the number of epochs from 1 to 5.

### Method 4: Testing by changing hyperparamters
In capsule network, some of the most important hyperparamters are:
- routing iterations r. After r times, all outputs for higher level capsules were calculated and routing weights have been established. The forward pass can continue to the next level of network. In the paper, Hinton et.al says using more iterations tends to overfit the data, so they recommend using 3 iterations.
- optimization method: Adam. We can use a different optimization method

### Method 5: Testing by using adversarial attack
From 2014, some research papers show that deep learning can be easiy fool by very low noise. In NIPS 2017 workshop, Ian Goodfellow opened adversarial non-targeted/targeted attack and defense competition for this problem. In ICLR 2018, lots of researches for adversarial examples are submitted. In this case, we try to validate the robustness of Capsule Network by using some well-known adversarial attack.
