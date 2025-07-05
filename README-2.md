
# Threshold Detection for Harsh Events Using Dynamic Time Warping and Machine Learning

## Project Overview

This project aims to leverage Dynamic Time Warping (DTW) to find the optimal threshold for detecting harsh events using sensor data. The approach involves computing DTW distances between reference sequences of harsh acceleration events and other labeled sequences. Various machine learning models are then used to determine the best DTW distance threshold for accurate classification.

The models employed include:
- Logistic Regression
- Random Forest
- Gradient Boosting
- Voting Classifier

## Dataset

The dataset used for this project  contains sensor readings and event labels. The dataset includes the following columns:

| **Column**       | **Description**                                         |
|------------------|---------------------------------------------------------|
| `time`           | Timestamp of the sensor reading.                       |
| `harsh_event`    | Type of event (e.g., sudden-acceleration, reverse-safe). |
| `time Difference`| Difference between consecutive timestamps.             |
| `Ax`             | Accelerometer reading in the x-axis.                   |
| `Ay`             | Accelerometer reading in the y-axis.                   |
| `Az`             | Accelerometer reading in the z-axis.                   |
| `Gx`             | Gyroscope reading in the x-axis.                       |
| `Gy`             | Gyroscope reading in the y-axis.                       |
| `Gz`             | Gyroscope reading in the z-axis.                       |

## Preprocessing

1. **Loading and Cleaning Data**
   - Load the dataset from Google Drive.
   - Convert the `time` column to datetime format.
   - Scale sensor data (`Ax`, `Ay`, `Az`, `Gx`, `Gy`, `Gz`) using Min-Max scaling.

2. **Feature Extraction**
   - Extract reference sequences for different harsh events.
   - Compute Dynamic Time Warping (DTW) distances between these reference sequences and other labeled sequences.

3. **Feature Engineering**
   - Compute mean and standard deviation for sequences based on DTW distances.

## Feature Sets

The following feature sets are used for model training and evaluation:

| **Feature Set** | **Description**                                          | **Features Included**                                    |
|-----------------|----------------------------------------------------------|----------------------------------------------------------|
| **Set 1**       | DTW distances for accelerometer and gyroscope readings  | `DTW_Ay_1`, `DTW_Ay_2`, `DTW_Ay_3`, `DTW_Ay_4`, `DTW_Ay_5`, `DTW_GyroZ_1`, `DTW_GyroZ_2`, `DTW_GyroZ_3`, `DTW_GyroZ_4`, `DTW_GyroZ_5` |
| **Set 2**       | Mean and standard deviation of the sequences            | `Mean_Sequence_Ay`, `Mean_Sequence_GyroZ`, `Std_Sequence_Ay`, `Std_Sequence_GyroZ` |
| **Set 3**       | Combination of all features                              | Features from Set 1 and Set 2 combined                   |

## Model Training and Evaluation

1. **Training Models**
   - Models used: Logistic Regression, Random Forest, Gradient Boosting, and Voting Classifier.
   - Train each model using the different feature sets.

2. **Evaluation Metrics**
   - Evaluate model performance using ROC curves and AUC scores.
   -  ![image](https://github.com/user-attachments/assets/eb715387-a104-445e-b5c3-67ff0cc19855)
3. **Feature importance**
   - visualization of the importance of different features using a plot
   - ![image](https://github.com/user-attachments/assets/add700b2-5a58-48d1-8177-77cfc7de1ee5)
3. **Threshold Selection**
   - Determine the optimal DTW distance threshold for classification based on ROC curve analysis.

## Code Usage

1. **Installation**
   - Install the required libraries using pip:
     ```bash
     pip install numpy pandas matplotlib scikit-learn plotly
     ```

2. **Running the Analysis**
   - Clone the repository or download the notebook.
   - Place `combined_data.xlsx` in the appropriate directory.
   - Execute the Jupyter notebook to perform data preprocessing, feature extraction, model training, and evaluation.

3. **Notebooks**
   
    The main analysis is performed in the Jupyter notebook         provided in this repository.There are two notebooks splitted in to two parts
   - Data preprocesssing 
   - Implementation of models to find the threshold

## Acknowledgements
- Libraries used: numpy, pandas, matplotlib, scikit-learn, plotly

For any questions or feedback at ['workayushiitk23@gmail.com']

