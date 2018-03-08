## Testing Capsule Network with different routing iterations

### Overview of routing iterations in dynamic routing of Capsule Network

Routing iterations is the number of times we need to repeat the dynamic routing algorithm to establish the agreement between low-level capsules with high-level capsules. 

![alt text](https://dasayan05.github.io/blog/res/1/dyn_route.jpg)
[Explaining routing iterations using clustering](https://dasayan05.github.io/blog/jekyll/update/2017/11/20/an-intuitive-understanding-of-capsules.html)

In the left image, all the points represents all the connections from the all low-level capsules to one high-level capsule only. In the first iterations, all connections are established. Then, repeating dynamic routing multiple times will find out a group of low-level capsules that strongly agree to each other. It can be shown in the right image, which is the second iteration of dynamic routing. Some points (light color points) are pruned out, and dark points are stayed. The fact that those dark points stayed together and formed a cluster means they represents the strong agreement (strong connections) from those low-level capsules to this high-level capsule. 

![alt text](https://image.slidesharecdn.com/capsulenetworks-171223023023/95/capsule-networks-27-638.jpg?cb=1514004058)

[Explaining routing iterations using connected layers](https://www.slideshare.net/charlesmartin141/capsule-networks-84754653)


This image explains the above routing iterations in another way using neural network context. At first, we assume all the low-level capsules (PrimaryCap) will be fully connected with high-level capsules (DigitCaps). After doing dynamic routing a few times, the connections from the low-level capsules (PrimaryCaps) to high-level capsules (DigitCaps) will not be fully connected anymore; instead, some of the connections are pruned, leaving all the connections that best matches outputs from the lower level capsules (PrimaryCaps) with outputs of higher level capsules (DigitCaps).

Therefore, after *r* times, all outputs for higher level capsules were calculated and routing weights have been established. The forward pass can continue to the next level of network

### How many routing iterations are sufficient?
In the paper, Hinton et al claims that more iterations tends to overfit the data and it is recommended to use 3 routing iterations in practice. To test his idea, we will try to train the Capsule Network with 3, 5, 10, 15 iterations and check the accuracy of the network to see if it is increased or not.

| Routing Iterations  | Accuracy |
| :---:               | :---:    |
| 3                   |          |
| 5                   |          |
| 10                  |          |
| 15                  |          |
