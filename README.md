# Surface Material Detection Using Haptic Force Data
This project explores various neural network models to identify materials using haptic force data from scratching on different surfaces. The data is collected using a UR10e robot with an ATI Force/Torque (F/T) sensor arm attachment.

# Project description
This project investigates diverse material classification techniques using force data acquired from scratching actions on various dry surfaces. Different neural network models are examined to achieve training and validation accuracy of approximately or exceeding 90%, alongside reduced training time. Additionally, the integration of frictional coefficients computed from straightforward non-differential physics equations is introduced as an auxiliary input feature. The findings also elucidate the impact of neural network batch size on accuracy and training time based on the size of the dataset.

<p align="center">
  <img src="https://github.com/user-attachments/assets/1dcac24e-89ca-4b9f-81e9-3f535412bb97" alt="Image 1" width="400" />
  <img src="https://github.com/user-attachments/assets/ffcb5c66-3747-4ded-af6a-cc87c903647c" alt="Image 2" width="400" />
</p>

# Datasets
Extract contents of Datasets.rar (collected using ATI FT34898 F/T Sensor) in the root folder. 
<br>For example: 2023-05-16_16-36-37_FT34898.csv file will be in following directory .\Datasets\log\Cardboard\1 newton\15 velo

**Note:** preprocessed dataset folder has not been included due to large size. It can be generated in local drive during Step 4 of running scripts in [Data PreProcessing.ipynb](https://github.com/nibrassajjad/surface-material-detection-using-haptic-force-data/blob/main/Data%20PreProcessing.ipynb).

# Quick Guide

### Data Preprocessing/Data Wrangling and Exploratory Data Analysis (EDA):

1. Extract whole project in local drive (if using Jupyter Notebook) or preferred environment.
2. Extract the Datasets.rar to the root folder as mentioned earlier.
3. Open [Data PreProcessing.ipynb](https://github.com/nibrassajjad/surface-material-detection-using-haptic-force-data/blob/main/Data%20PreProcessing.ipynb).
4. Run through the cell scripts. Each cell's function is explained within the notebook (primarily data wrangling cells, with the last few cells containing graphical plots for EDA tasks).
5. To view correlation between different parameters for each individual material run the script in [Correlation file generator.ipynb](https://github.com/nibrassajjad/surface-material-detection-using-haptic-force-data/blob/main/Correlation%20file%20generator.ipynb) for further EDA purpose. The matrix file will be in the defined output directory.

### Running neural network models:

Different kind of neural network model variations have been created for performance analysis. The notebook can be found at [./ML models/filtered/ML model.ipynb](https://github.com/nibrassajjad/surface-material-detection-using-haptic-force-data/blob/main/ML%20models/filtered/ML%20model.ipynb)

# Project Approach

## Methodology

![image](https://github.com/user-attachments/assets/794ff211-7074-4d8c-8607-a35502ded9c9)

## 1. Data Collection and Preprocessing/Wrangling

UR10e robot arm with ATI FT34898 F/T Sensor attachment was used to scratch vertically on 10 different materials at various programmed speed and normal force. The haptic action of scratching was performed back and forth along x-axis for 50 mm. Force data at the metal tip was recorded in X, Y, Z-axis during the haptic exploration. 

**Note:** A quick manual on how to use ATI F/T Force Sensor can be found [here](https://github.com/nibrassajjad/surface-material-detection-using-haptic-force-data/blob/main/FT_sensor_manual.pdf)

![image](https://github.com/user-attachments/assets/e98e14bc-8b0e-4448-a0c0-5c75d3b03998)

* **Raw data:** Total number of raw data points recorded: 423550 from 600 datasets (60 for each material)
* **Feature Engineering:** Frictional coefficient and Tangential force for every data point is computed
* **Data Filtering:** Outlier removal by retaining data between 1st and 3rd quartile of frictional coefficient only
* **Filtered Data** Total number of data points after filtering: 289485 (~68% of raw dataset)
* **Data Enrichment:** Variance, correlation coefficients, variance per sample, correlation per sample for forces in x,y,z axis is also computed for every filtered dataset
* **Statistical Summary:** A statistical summary dataset is created which have average values of all the entries in every dataset. This statistical summary dataset will be used mainly for our [machine learning models 1-6](https://github.com/nibrassajjad/surface-material-detection-using-haptic-force-data/blob/main/ML%20models/filtered/ML%20model.ipynb).

![image](https://github.com/user-attachments/assets/c0d24e08-46d7-464c-a4c6-8917cbd4dcf3)

## 2. Training neural network models

* Eight different neural network models have been trained for evaluation. The code for these models can be found [here](https://github.com/nibrassajjad/surface-material-detection-using-haptic-force-data/blob/main/ML%20models/filtered/ML%20model.ipynb)
* Model 1,2,3,4,5,6 uses the statistical summary set as the network's input.
* The dataset is split into a training set and a test set with an 80%:20% ratio.
* Since the statistical summary dataset contains only 600 entries, the batch size for training the algorithm is set to 1 (for Model 1 through 6).
* The training set is further divided into a training set and a validation set with a 90%:10% split. A validation set is necessary to ensure that the model does not overfit.








