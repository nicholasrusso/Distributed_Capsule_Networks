## Usage of Horovod within our Project

In order to use [Horovod](https://github.com/uber/horovod), the additions that we needed to make to our program were surprisingly minimal. A simple function call initializes our Horovod environment. After that, each process is assigned a single GPU along with a local rank. This local rank is essentially the ID of the process, and is used to determine which GPU each process uses. The next step is to build the model itself, which in our case is a capsule network model, and to scale the learning rate of this model depending on the number of computers we have within our distributed system. Any optimizers we create for our model are wrapped in the "DistributedOptimizer" class, which allows each process to use the original optimizer to compute gradients, averages these gradients using a call to MPI such as "allreduce" or "allgather", and applies the averaged gradient. We then choose the value that we want to minimize, allow our program to save checkpoints on one of the machines in our system, and start the training session with the creation of a "MonitoredTrainingSession" tensorflow object. Finally, to run the Horovod program we created, we use standard MPI command line executables. 

![alt text](https://user-images.githubusercontent.com/16640218/34506318-84d0c06c-efe0-11e7-8831-0425772ed8f2.png)