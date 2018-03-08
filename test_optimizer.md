## Testing Capsule Network Using different optimizers

Optimization algorithms are the engines that power neural networks in general and enable them to learn patterns from data. Similar to the normal neural network, capsules network need to learn the Weight matrix (Wi,j). The most common algorithm used to train neural networks and deep learning models is gradient descent. Gradient descent has many variants, but, in each case, the idea is the same: iteratively evaluate paramters, compute the loss, then take a small step in the direction that will minimize the loss.

### Gradient Descent
#### Standard Vanilla Gradient Descent
Vanilla gradient descent performs only one weight update per epoch, making it very slow (if not impossible) to converge on large datasets. We do not use this standard gradient descent to update since it takes a long time to train the capsule network on large datasets. The reason for this slowness is because each iteration of gradient descent requries us to compute a prediction for each training point in our training data before we are allowed to update the weight matrix.

#### Stochastic gradient descent (SGD)
SGD applies multiple weight updates per epoch by computing the gradient on small mini-batches of training data, instead of the entire training set. To yield a batch, we sample our data, usually by randomizing the training samples before applying SGD since the algorithm is quite sensitive to batches. 
```python
while True:
   batch = next_training_batch(data, batch_size)
   Wgradient = evaluate_gradient(loss, batch, W)
   W += -alpha * Wgradient
```
While this modification leads to "more noisy" updates, it also allows us to take more steps along the gradient (1 step/each batch vs 1 step/epoch), ultimately leading to faster convergence and no negative affects to loss and classification accuracy. By using SGD we can dramically reduce the time it takes to train a model. Usually, SGD will get the model with lower loss and higher accuracy. In our testing, we will use SGD to test the capsule network.

### SGD with Momentum
The goal of the momentum is to build upon the standard weight update to include a momentum term to allow the model to obtain lower loss and higher accuracy in less epochs. The momentum should increase the strength of updates for dimensions who gradients point in the same direction and then decrease the strength of updates for dimensions who gradient switch directions.
```python
v = gamma * v - alpha * dW
W += v
```

### Adaptive Learning Rate Methods
SGD modifies all parameters in a network equally in proportion to a given learning rate. However, given that the learning rate of a network is the most important hypyerparameter to tune and a hard tedious hyperparameter to set correctly, many people have suggest to adaptively tune the learning rate as the network is trained

#### Adagrad
First introduced by Duchi et al [1], Adagrad adapts the learning rate to the network parameters. Larger updates are performed on parameters that change infrequently while smaller updates are done on parameters that change frequently. 
```python
cache += (dW ** 2)
W += -lr * dW / (np.sqrt(cache) + eps)
```
Weights that have frequently updated/large gradients in the cache will scale the size of the update down, or lower the learning rate for the parameter. On the other hand, weights that have infrequent updates/smaller gradients in the cache will scale up the size of the update, or raise the learning rate for the specific parameter.

Advantage of Adagrad is that we no longer have to tune the learning rate. In the test, we will use the initial learning rate at 0.01 and allow the adaptive nature of the algorithm to tune the learning rate on a per-parameter basis. However, the drawback of Adagrad is from the accumulated cache. It will keep monotomously growing during the training process, and dividing a small number (the gradient0 with large number (the cache) will result in an update that is really small, too small for the network to actually learn anything in later epochs.

#### Adadelta
The Adadelta algorithm was proposed by Zeiler et al [2]. Adadelta can be seen as an extension to Adagrad that seeks to reduce the decreasing learning rated in later epochs.

#### RMSprop
RMSprop algorithm is an (unpublised) optimization algorithm shown in the slides of Geoffrey Hinton's coursera class.
```python
cache = decay_rate * cache + (1 - decay_rate) * (dW ** 2)
W += -lr * dW / (np.sqrt(cache) + eps)
```
RMSprop also attempts to rectify the negative effects of globally accumulated cache by converting the cache into an exponentially weighted moving average. The "moving average" aspect of RMSprop allows the cache to "leak out" old squared gradients and replace them with newer "fresher" ones. This will aboid monotonically decreasing learning rates during training process.

#### Adam
Adam (Adaptive Moment Estimation) is essentially RMSprop with momentum added to it:
```python
m = beta1 * m + (1 - beta1) * dW
v = beta2 * v + (1 - beta2) * (dW ** 2)
x += -lr * m / (np.sqrt(v) + eps)
```
The value of both m and v are similar to SGD momentum, relying on their respective previous values from time t - 1. the value m represents the first moment (mean) of the gradients while v is the second moment (variance). The actual update to W is near identical to RMSprop, only now we use the "smoothed" version of m rather than the raw gradient dW.

### Testing Capsule Network with different optimizers
To start off, we will use the following optimizers:
* SGD with momentum
* RMSprop
* Adam
Those optimizers are the most currently in deep learning models.
