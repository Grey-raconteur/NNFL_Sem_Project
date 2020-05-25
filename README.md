# NNFL_Sem_Project
Implementing U-net on Drive Dataset

### Steps to Run
1. Add the DRIVE DataSet in the follwing directory structure.
DRIVE<br>
│<br>
└───test<br>
|    ├───1st_manual<br>
|    └───2nd_manual<br>
|    └───images<br>
|    └───mask<br>
│     <br>
└───training<br>
    ├───1st_manual<br>
    └───images<br>
    └───mask<br>

2. Run the follwing commands:
```python
  python prepare_datasets_DRIVE.py
  python run_training.py
  python run_testing.py
```

### Pre-requisites
- numpy >= 1.11.1
- PIL >=1.1.7
- opencv >=2.4.10
- h5py >=2.6.0
- ConfigParser >=3.5.0b2
- scikit-learn >= 0.17.1

### Working
The training of the neural network is performed on sub-images (patches) of the pre-processed full images. Each patch, of dimension 48x48, is obtained by randomly selecting its center inside the full image. Also the patches partially or completely outside the Field Of View (FOV) are selected, in this way the neural network learns how to discriminate the FOV border from blood vessels.
A set of 190000 patches is obtained by randomly extracting 9500 patches in each of the 20 DRIVE training images. Although the patches overlap, i.e. different patches may contain same part of the original images, no further data augmentation is performed. The first 90% of the dataset is used for training (171000 patches), while the last 10% is used for validation (19000 patches).<br>

The neural network architecture is derived from the U-net architecture (see the paper). The loss function is the cross-entropy and the stochastic gradient descent is employed for optimization. The activation function after each convolutional layer is the Rectifier Linear Unit (ReLU), and a dropout of 0.2 is used between two consecutive convolutional layers.
