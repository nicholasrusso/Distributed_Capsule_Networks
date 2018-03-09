# An Overview of Distributed Capsule Networks
Our goal over the past ten weeks was to explore the feasibility 
of distributing capsule networks. While capsule networks take far less data to train, they are slow to train. 
From our experiments, we were able to distribute the training process and acheive comparable results to 
other non-distributed open source projects.

## Experiment Overview
For our experiments, we used computers from the High Performance Computing Lab at 
California Polytechnic State University, San Luis Obispo. We had up to 20 computers 
running during our experiments, all having the same configuration. These computers 
were configured with Intel(R) Xeon(R) E5-2620 processors and Nvidia GeForce GTX 980 
graphics cards. For our environment, we are using Python 3.5.5, TensorFlow 1.5.0, 
Keras 2.1.4, and Horovod 0.11.3. 

## Our Results
The main goal of this paper was to determine if training capsule networks could be 
distributed while maintaining their high accuracy from a low number of training images. 
To do this, we perform a threefold experiment. Prior to the experiments, we ran the 
original Keras capsule network implementation using the CPU and GPU version of 
Tensorflow to get a benchmark of 10.1 minutes and 6.5 minutes per epoch. We trained a 
capsule network 4 separate times with 5 epochs on 1, 5, 10, and 15 machines and compared 
the results against our benchmark. Our first experiment was CPU based since our TensorFlow 
and Horovod versions were initially not optimized for use of the available GPU’s. Unsurprisingly, 
this was our slowest configuration, but the total training time did decrease with the total number 
of machines used. With 15 machines, we were able to decrease the training time from 610 seconds 
per epoch to 88 seconds per epoch. Our second experiment used a GPU version of TensorFlow and a 
CPU version of Horovod. In these experiments, we saw significant speed ups. Our best result was 
able to match the original implementations accuracy while reducing the training down to 60 seconds 
with 15 machines. Our third experiment used a GPU version of TensorFlow and a GPU version of
Horovod using NCCL 2 for all-reduce functions. The results from this experiment were similar 
to the second experiment but the reduction of the distributed model completed significantly 
faster. From all of these experiments, our accuracy was similar to all of the open source non-distributed versions.
While we weren't able to match the same results as the orginal paper, we still believe this 
experiment was a success considering (to the best of our knowledge) no other open source capsule network
has been able to match the original papers results. In summary, our results averaged at 99.65% accuracy 
on our validation test set and acheive a maximum accuracy of 99.7% accuracy. These averages were taken
from training over 100 epochs 3 times. From these experiments, we can see that distributing capsule networks significantly 
decreases the total training while maintaining similar accuracy.
