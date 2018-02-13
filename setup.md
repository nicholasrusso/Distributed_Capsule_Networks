## Xifeng Guo's Capsule Network Implementation Setup

### Language
- Python 3.5 or above.

### Package Install Command
- pip install <package> or whatever pip is linked to Python 3.5 or above.

### Required Packages and Versions
- tensorflow (>= 1.2)
- tensorflow-gpu (>= 1.5)
- image (>= 1.5.17)
- h5py (>= 2.7.1)
- six (>= 1.11.0)
- keras (>= 2.1.3)
- matplotlib (>= 2.1.1)
- numpy (>= 1.14.0)

### For Multiple GPU Support
- Cuda
- CuDNN
  
### For Distributed Training (Not included in original implementation)
- Apache Spark
- Make sure all packages are install on all of the machines.


### Trouble Shooting
#### General Installation
- Your pip version may be linked to a different a different python version. If you are using Python 3.5.5 you need your pip to be linked to Python 3.5.5. Packages do not transfer between python packages so you'll have to install the packages again.
#### Numpy
- Sometime you can have multiple versions of numpy installed. Uninstall the older numpy version and make sure your current version is updated appropriately.
#### Tensorflow/Keras
- If you are having trouble import tensorflow or keras, make sure your python version is above 3.5. 
- If you are using a computer with a GPU, make sure you have Cuda and CuDNN installed. Also, make sure your LD_LIBRARY_PATH evironment variable is set to something similar to export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/extras/CUPTI/lib64
#### Spark
- TBD

