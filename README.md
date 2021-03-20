# Data Science vs. Pump It Up Competition

Tanzania is the largest country in East Africa within the African Great Lakes region, with a population of 59 millions people. Like many poor nations around the world, Tanzania suffers from serious issues involving not having access to clean water. The Tanzanian Water Ministry agreed with Taarifa and they began a competition by DrivenData to solve this problem by improving clean water sources. This project involved using information given about water-points in Tanzania to predict whether or not a given water source (wells, pumps, standpipes, fountains, boreholes, etc.) was working correctly.

There are 3 different datasets: training set, test set and train labels set which contains the status of wells. 

* The given data included a target with three classes — ‘functioning’, ‘non-functioning’, and ‘functioning needs repair’. 
* The train & test set contain 59400 water points data with 40 features.

The idea was to build a model that could predict if a given water-point would fall into one of these three classes. 

## Business Statement

**Q1.** 

**Q2.** 

**Q3.**

## The Deliverables

There are 5 deliverables for this project:

1. A well documented Jupyter Notebook containing any code and comments explaining it.

            - Part I: EDA
            
            - Part IIA: Models
            
            - Part IIB: Models without Correcting Class Imbalance
            
2. An organized README.md file that describes the contents of the repository.

             - README.md: describes the content and organization of content.
             - module3_project_rubric.pdf: describes requirements for this project.
             - Data folder: contains all provided data and all figures for visualization.
             - Part I: Jupyter notebook
             - Part IIA: Jupyter notebook
             - Part IIB: Jupyter notebook
             - Presentation pdf

3. A short PowerPoint presentation (delivered as a PDF export) giving a high-level overview of the methodology used and recommendations for non-technical stakeholders. Can be found in the repository or at: 



4. A Blog Post which can be found at: 



5. A Video Walkthrough of my non-technical presentation, can be found at:



# **Notebook Table of Contents**

## PART I: EDA

Data sources:
      
            - https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/

<img src = '../main/Data/status_group_countplot.png' />

## PART IIA: Modelings

## PART IIB: Modelings without Correcting Class Imbalance

|FIELD1|Model                        |Accuracy|CV  |Precision|Recall|F1 Score|MAE |MSE |RMSE|AUC |Bias                |Variance           |
|------|-----------------------------|--------|----|---------|------|--------|----|----|----|----|--------------------|-------------------|
|0     |Imbalance Decision Tree      |75.96   |0.72|0.65     |0.66  |0.65    |0.27|0.32|0.57|-   |0.011531986531986532|0.363859236302418  |
|1     |Imbalance Logistic Regression|74.87   |0.74|0.68     |0.56  |0.58    |0.27|0.3 |0.55|0.82|0.0117003367003367  |0.24931604909929822|
|2     |Imbalance KNN                |78.96   |0.73|0.7      |0.66  |0.68    |0.23|0.27|0.52|-   |0.007744107744107744|0.31581343740434636|
|3     |Imbalance Bagged Tree        |79.16   |0.76|0.69     |0.66  |0.67    |0.23|0.27|0.52|-   |-0.014225589225589226|0.32314757422711965|
|4     |Imbalance Random Forest      |80.35   |0.77|0.77     |0.63  |0.66    |0.21|0.24|0.49|-   |0.0031986531986531986|0.2651576369758188 |
|5     |Imbalance Gradient Boost     |81.3    |0.78|0.73     |0.68  |0.7     |0.2 |0.24|0.49|-   |0.00202020202020202 |0.30902626149259155|
|6     |Imbalance ADABoost           |71.8    |0.72|0.6      |0.51  |0.5     |0.3 |0.32|0.57|-   |0.01717171717171717 |0.22208615334036214|
|7     |Imbalance XGBoost            |80.45   |0.78|0.77     |0.63  |0.66    |0.21|0.24|0.49|-   |0.0017676767676767678|0.26467451592241154|
|8     |Imbalance SVM                |78.54   |0.76|0.75     |0.6   |0.63    |0.23|0.26|0.51|-   |0.022643097643097642|0.25001524079175597|

##  Summary of Key Findings

<img src = '../main/Data/decision_tree_clf_feature_importances.png' />

##  Summary of Actionable Insights

##  Future Works
1. Try more parameters tuning with more and wider range of options
2. Work to reduce overfit while maintaining and/or improving accuracy score
