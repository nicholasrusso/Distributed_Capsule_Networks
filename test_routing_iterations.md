## Testing Capsule Network with different routing iterations

Routing iterations is the number of times we need to repeat the dynamic routing algorithm. At first, we assume all the low-level capsules (PrimaryCap) will be fully connected with high-level capsules (DigitCaps). After doing dynamic routing a few times, the connections from the low-level capsules (PrimaryCaps) to high-level capsules (DigitCaps) will not be fully connected anymore; instead, some of the connections are pruned, leaving all the connections that best matches outputs from the lower level capsules (PrimaryCaps) with outputs of higher level capsules (DigitCaps)

![alt text](https://dasayan05.github.io/blog/res/1/dyn_route.jpg)

