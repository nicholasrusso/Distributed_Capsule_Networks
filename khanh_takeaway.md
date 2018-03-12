## Takeaway

This blog will summarize what I learn throughout the quarter about capsule network.

### Problem with CNN
#### Spatial relationship among parts of objects
Internal data structure of CNN does not take into consideration the spatial hierarchies between simple and complex objects. For examples, if in the image, there is 2 eyes, a mouth, a nose, it does not mean there is a face in the image.

#### Inverse Graphic
When we see an object, we deconstruct the object hierarchically and match it with known patterns inside our brains. That is the reason we can regconize the object. Since the representation of objects in our brain does not depend on viewpoint, we can easily recognize the object even though the images can be taken from different angle. CNN does not do inverse graphic

##ax pooling is bad
In CNN, we try to achieve viewpoint invariant in the activities of neuron using max pooling. It means from low-level layer, we will consecutively looks at each region and select the most active / largest number in each region. Conceptually, we want when we changing the input a little, the output still stays the same. This mechanism is not good because we will lose a lot of valuable information. It also does not encode the spatial relationship between features.

### Solution with Capsule Network
#### Use capsule to group neuron into vector
Capsule network solves that issue by grouping neurons into capsules, which is a vector that represent (1) the presence of the object in the image and (2) pose of the objects (position, orientation, rotation, skewness...). In other words, the CapsNet explicitly encodes those information inside its model. Using capsule, we can store all important information in the form of vector.

#### Train capsule network using dynamic routing
Low level capsule will send its input to higher level capsule that "agree" with its input. The high-level capsule tries to cluster the low-level input that are correlated to each other.





