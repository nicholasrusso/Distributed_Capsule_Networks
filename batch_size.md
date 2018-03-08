### Batch Size vs. Epoch vs. Iterations

When I was first introduced to machine learning and specifically neural networks, my peers and professors threw around the terms "batch size" and "epochs". Being fairly new to data science, I easily got confused between the two. My objective for this post is to explain and clearly define the difference between batch size, epochs, and iterations.

#### Batch Size
Batch size is defined as the total number of training samples that are going to be propagated through the network. For example, the MNIST dataset consists of 60,000 training images. Our first set of experiments ran with a default batch size of 100, so our capsule network trained on 600 images (60,000/100 = 600) and gave each machine a subset of this training set. For example, distributing the training across 5 machines meant that each machine was given 120 images. 

#### Epoch
The number of epochs is the total number of times the complete dataset is passed forward and back through the network. So one epoch is when one forward pass and one backward pass of all the training samples have gone through the network one time. 
Note that because you typically can't pass the entire dataset through your network in one swoop, splitting your data into the appropriate number of batches. 
Anyways, as you run more and more epochs, your error decreases and your accuracy increases. However, running too many epochs puts you at risk for overfitting your model.

#### Iterations
Finally, the number of iterations is defined as the number of batches to complete one epoch. In other words, it is the number of forward + backward passes through the training set. So in our case of 60,000 images and a batch size of 100, it would take 600 iterations to complete one epoch. However, since one of the main advantages of capsule networks is that they take less data to train, our network is trained on 600 images as the "entire training set" - so our network only ever sees 600 images.

Hopefully this clarified the differences between batch size, epochs, and iterations are!
