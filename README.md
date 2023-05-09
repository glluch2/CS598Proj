# CS598Proj - Paper 164 - Design and implementation of a deep recurrent model for prediction of readmission in urgent care using electronic health records.

Paper:
T. Zebin and T. J. Chaussalet, "Design and implementation of a deep recurrent model for prediction of readmission in urgent care using electronic health records," 2019 IEEE Conference on Computational Intelligence in Bioinformatics and Computational Biology (CIBCB), Siena, Italy, 2019, pp. 1-5, doi: 10.1109/CIBCB.2019.8791466.

Dependencies: 
pandas
numpy
matplotlib
seaborn
sklearn
scipy
xgboost
lightgbm
tensorflow
focal_loss

Data download instruction: 
- instructions here: https://eicu-crd.mit.edu/gettingstarted/access/
- complete “Data or Specimens Only Research” course.
- follow steps at bottom of page: https://physionet.org/content/mimiciii/1.4/ and download dataset

This repo contains a number of notebooks. We recommend that in order to reproduce, you upload these and emulate the file structure in Google Drive, or change the directory variables to whatever you want. The drive must contain the MIMIC-III files. The files used are:
- CHARTEVENTS.csv
- ADMISSIONS.csv
- PATIENTS.csv
- TRANSFERS.csv
- D_ITEMS.csv
- DIAGNOSES_ICD.csv

Preprocessing: 
- assign_class_labels.ipynb - This notebook handles the computation of target labels for ICU cases. Once labels are assigned, they are saved for later to merge with the train set.
- prune_chartevents.ipynb - This handles pruning of the considerably large CHARTEVENTS.csv from the source dataset. Chartevents are filtered according to certain ITEMIDs mentioned in the paper. Additionaly, only the last 48 hours of chart events records are kept for each ICU stay. This reduces the size of the dataset considerably. Results are saved as chartevents_pruned.csv and used in the next step.
- build_dataset.ipynb - This handles construction of the train set. Pruned chartevents are pivoted and assigned to ICU stays. ICD9 Diagnoses are grouped into broad categories and assigned to patient hospital admissions. Label vector is read and assigned to the dataset.

Training and results: 
- medi_final.ipynb handles training and performance metrics 

CNN results:
![image](https://user-images.githubusercontent.com/112778741/236985933-a85cbf0c-c4ce-420c-86d4-bcc06f426428.png)
![image](https://user-images.githubusercontent.com/112778741/236985985-d50431b1-cb50-4ade-ad97-7a2cf19aa80d.png)

LSTM results: 

