# Surface material detection using haptic force data
This project contain different models to identify amongst 10 different materials using haptic force data from scratching on the surfaces using UR10e robot.

# Datasets
Extract contents of Datasets.rar in the root folder. 
(E.g. 2023-05-16_16-36-37_FT34898.csv file will be in following directory .\Datasets\log\Cardboard\1 newton\15 velo )

Note: preprocessed dataset folder has not been included due to large size.

# Getting started

Analyzing and processing the data:

1. Extract the Datasets.rar to the root folder as mentioned earlier.
2. Open Data PreProcessing.ipynb.
3. Run through the scripts. What each cell does is explained within the notebook.
4. To view correlation between different parameters for each individual material run the script in Correlation file generator.ipynb. The matrix file will be in the defined output directory.

Running neural network models:

Different kind of neural network model variations have been created for performance analysis. The notebook can be found at ./ML models/filtered/ML model.ipynb
