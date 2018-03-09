# Optimizers
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
![sgdvsgd2](https://pengcheng.tech/wp-content/uploads/2017/09/Screen-Shot-2017-09-28-at-22.59.03.png)
![sgd vs gd](http://www.bogotobogo.com/python/scikit-learn/images/Batch-vs-Stochastic-Gradient-Descent/stochastic-vs-batch-gradient-descent.png)


# Stochastic Gradient Descent Optimizers

## Momentum
Momentum is an optimizing on top of stochastic gradient descent.
SGD has issues with getting trapped in a local minimum and taking a long time to go down a steep gradient. 
In momentum, if a steep gradient is calculated, "momentum" is gained and you take a larger step down the gradient. If 
the gradient changes direction, momentum is lowered. Essentially, a percentage of your last movement is added to your
current movement down the gradient.
Imagine a ball being pushed down a hill. As the ball moves down the hill, it goes faster and faster. 
If the hill levels out, the ball slows.
![mom](http://slideplayer.com/8731569/26/images/38/Enhancements+To+Gradient+Descent.jpg)

## Adam
The Adam optimizer uses a combination of the Momentum and RMSProp optimizer. 
The RMSProp optimizer is an adaptive learning rate optimizer. At each step, RMSProp divides
the learning rate by the expontential decay of the squared gradients. The Adam optimizer stores
the average of past squared gradients(RMSProp) in addition to average of past gradients (Momentum)

![comparison](http://2.bp.blogspot.com/-q6l20Vs4P_w/VPmIC7sEhnI/AAAAAAAACC4/g3UOUX2r_yA/s1600/s25RsOr%2B-%2BImgur.gif)

### References
[Gradient descent algorithms and adaptive learning rate adjustment methods](https://towardsdatascience.com/gradient-descent-algorithms-and-adaptive-learning-rate-adjustment-methods-79c701b086be)


[Gentle Introduction to the Adam Optimization Algorithm for Deep Learning](https://machinelearningmastery.com/adam-optimization-algorithm-for-deep-learning/)


[An overview of gradient descent optimization algorithms](http://ruder.io/optimizing-gradient-descent/index.html#gradientdescentvariants)


