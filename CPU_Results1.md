### Results - CPU Tensorflow
Here are some results running on various numbers of machines on various numbers of epochs using the CPU versions of Tensorflow and Horovod since at this point in time, they were not initially optimized to use GPUs.

#### 5 machines, 1 epoch:
Each machine gets 120 images
Average accuracy: 0.97388 avg
Time: 184.4s/epoch, 2s/step

#### 5 machines, 5 epochs:
Average accuracy per epoch: 
- Epoch 1: 0.97142
- Epoch 2: 0.98610
- Epoch 3: accuracy did not improve
- Epoch 4: 0.98966
- Epoch 5: 0.99250
Time: 2s/step

#### 15 machines, 1 epoch:
Each machine gets 40 images
Average accuracy: 0.316253
Time: 88s/epoch, 2s/step

#### 15 machines, 5 epochs:
Average accuracy per epoch:
- Epoch 1: 0.76042
- Epoch 2: 0.960746
- Epoch 3: accuracy did not improve
- Epoch 4: 0.97889
- Epoch 5: 0.98614
Time: 2s/step

There is a clear decrease in total training time from 5 to 15 machines, from 184.4 seconds per epoch when running on 5 machines to only 88 seconds when running with 15.
