## Optimizers
Gradient descent is a vital for any type of neural network. 
Both shallow and deep networks use gradient descent to "learn". In this blog post, 
we will discuss the progression from the orginial gradient descent to the Adam Optimizer.

## A Quick Overview of Gradient Descent
Gradient descent is one of the most popular methods for optimizing performance. 
In this algorithm, we calculate the gradient of the cost function with 
respect to theta. Our goal is to minimize of cost function. 
Our learning rate determines how much we step down our gradient. We continue to do 
this until a local minimum has been reached. This can be performed on either the entire 
training set multiple times or in smaller sub batches of the training data.

## Stochastic Gradient Descent
Stochastic Gradient Descent is very similar to gradient descent but it updates it's direction
down the gradient on each update training step. While gradient descent has a more direct path to the local 
minimum, stochastic gradient descent is not as computationally intensive and can converge on the local minimum 
faster.

## Stochastic Gradient Descent Optimizers

## Momentum
Momentum is an optimizing on top of stochastic gradient descent.
SGD has issues with getting trapped in a local minimum and taking a long time to go down a steep gradient. 
In momentum, if a steep gradient is calculated, "momentum" is gained and you take a larger step down teh gradient. If 
the gradient changes direction, momentum is lowered.
Imagine a ball being pushed down a hill. As the ball moves down the hill, it goes faster and faster. 
If the hill levels out, the ball slows.

## Adam
The Adam optimizer uses a combination of the Momentum and RMSProp optimizer. 
The RMSProp optimizer is an adaptive learning rate optimizer. At each step, RMSProp divides
the learning rate by the expontential decay of the squared gradients. The Adam optimizer stores
the average of past squared gradients(RMSProp) in addition to average of past gradients (Momentum)

### References
[Gradient descent algorithms and adaptive learning rate adjustment methods](https://towardsdatascience.com/gradient-descent-algorithms-and-adaptive-learning-rate-adjustment-methods-79c701b086be)


[Gentle Introduction to the Adam Optimization Algorithm for Deep Learning](https://machinelearningmastery.com/adam-optimization-algorithm-for-deep-learning/)


[An overview of gradient descent optimization algorithms](http://ruder.io/optimizing-gradient-descent/index.html#gradientdescentvariants)


