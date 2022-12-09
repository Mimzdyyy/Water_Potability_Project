# Water Potability

## 1. Goal of the project

Develop a solution to predict the potability of the water based on the different water quality metrics.

The software will be implemnted in a hand device. 

## 2. Business Understanding and Business Problem

### Company occupation
Water For All is a global NGO specialized on granting access to potable water in disadvantaged areas.

### Business Problem
Water For All  wants to create a hand device to analyze the potability of water. 

## 3. Dataset

The dataset shape is:  10 Columns & 3276 rows

| Feature 1 | Feature 2 | Feature 3 | Feature 4 | Feature 5 | Feature 6 | Feature 7 | Feature 8 | Feature 9 |
| :-----: | :---: | :---: | :-----: | :---: | :---: | :-----: | :---: | :---: |
| pH | Hardness | Solids | Organic_carbon | Turbidity | Chloramines | Sulfate | Conductivity | Trihalomethanes |

| Target |
| :-----: |
| Potability |

Data Set found in Kaggle. 
[Kaggle link](https://www.kaggle.com/datasets/adityakadiwal/water-potability?resource=download&select=water_potability.csv)

## 4. Proccess

### 4.1 Exploratory Data Analysis

The Target Varible "Potability" is imbalance. It was decided to keep the imbalance to better predict the non potable water. Non potable water could be a risk for the water consumer

<img src="https://github.com/isra-st/Water_Potability/blob/master/Viz/Percentage_Potable_VS__non_Potable.png" alt="Test_VS_Prediction" width="500" height="300"> 

### Is it possible to predict the potability of water based on the confidence intervals of the features for potable and non potable datapoints? 

We raised this question to check if it was possible to decrease the hardware costs of the hand device by using filters for the samples instead of Classications models.

<img src="https://github.com/isra-st/Water_Potability/blob/master/Viz/ph.png?raw=true" alt="PH" width="250" height="200"> <img src="https://github.com/isra-st/Water_Potability/blob/master/Viz/sulfate.png?raw=true" alt="Sulfate" width="250" height="200"> <img src="https://github.com/isra-st/Water_Potability/blob/master/Viz/chloramines.png?raw=true" alt="Chloramines" width="250" height="200">

The Confidence Interval ranges for the potable and non potable datapoints overlap. It is not possible predict the potability of water based on filters. 

### 4.2 Modeling

#### Scores 

The Scores which guide the decisions 

* Recall (sensitivity) is the ratio of correctly predicted positive (potable water) observations to the all observations in the actual class potable.

* F1 Score is the weighted average of Precision and Recall. Therefore, this score takes both false positives and false negatives into account. 

The above scores have been chosen because we want to have a low number of False Positives and high number of True Positives.

#### Feature Engineering | Model Selection | Model Hypertunning | Loop

* The Scaler used for the model selection was Standard Scaler.

| Model 1| Model 2 | Model 3 | Model 4 | Model 5 | Model 6 | Model 7 |
| :-----: | :---: | :---: | :-----: | :---: | :---: | :-----: |
| Decision Tree Scaled | Decision Tree | KNN | SVM | Random Forest | Random Forest Scaled | Logistic Regression |

<img src="https://github.com/isra-st/Water_Potability/blob/master/Viz/Model_Selection_Recall.png?raw=true" alt="Recall" width="275" height="225"> <img src="https://github.com/isra-st/Water_Potability/blob/master/Viz/Model_Selection_F1_Score.png?raw=true" alt="F1_Score" width="275" height="225">

<img src="https://github.com/isra-st/Water_Potability/blob/master/Viz/confusion_Matrix_not_scaled_DecisionTreeClassifier().png?raw=true" alt="Decision_Tree_Not_Scaled" width="250" height="200"> <img src="https://github.com/isra-st/Water_Potability/blob/master/Viz/confusion_MatrixDecisionTreeClassifier().png?raw=true" alt="Decision_Tree" width="250" height="200">  <img src="https://github.com/isra-st/Water_Potability/blob/master/Viz/confusion_MatrixKNeighborsClassifier().png?raw=true" alt="KNN" width="250" height="200">

#### Conclussions Model Selection: 

* Decision Tree Scaled got the best scores for Recall and F1 Score. 
* The confusion Matrixs for Decision Tree Scaled and Decision Tree not Scaled are very similar.
* KNN confusion Matrix gives a low number of False Posivite that was one of the model goals but the True Positives are too low. It will not be usefull for the Hand Device

#### Decision Tree Scaled is the best choice at this stage. 

### 5 Presentation
To see the presentation, click in the below picture.

[<img src="https://github.com/isra-st/Water_Potability/blob/master/Viz/PPT%20_Picture.JPG?raw=true" alt="Water_Potability Presentation" width="500" height="330">](https://docs.google.com/presentation/d/1fwm4fuR3SZ9PEzHP4Mbbs-JDGXuuadtX9ty0v6nTuyI/edit#slide=id.p)

