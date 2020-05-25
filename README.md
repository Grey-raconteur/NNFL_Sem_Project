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
