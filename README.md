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

**Note:** preprocessed dataset folder has not been included due to large size.

# Quick Guide

### Data Preprocessing/Data Wrangling and Exploratory Data Analysis (EDA):

1. Extract whole project in local drive (if using Jupyter Notebook) or preferred environment.
2. Extract the Datasets.rar to the root folder as mentioned earlier.
3. Open [Data PreProcessing.ipynb](https://github.com/nibrassajjad/surface-material-detection-using-haptic-force-data/blob/main/Data%20PreProcessing.ipynb).
4. Run through the cell scripts. Each cell's function is explained within the notebook (primarily data wrangling cells, with the last few cells containing graphical plots for EDA tasks).
5. To view correlation between different parameters for each individual material run the script in [Correlation file generator.ipynb](https://github.com/nibrassajjad/surface-material-detection-using-haptic-force-data/blob/main/Correlation%20file%20generator.ipynb) for further EDA purpose. The matrix file will be in the defined output directory.

### Running neural network models:

Different kind of neural network model variations have been created for performance analysis. The notebook can be found at [./ML models/filtered/ML model.ipynb](https://github.com/nibrassajjad/surface-material-detection-using-haptic-force-data/blob/main/ML%20models/filtered/ML%20model.ipynb)


