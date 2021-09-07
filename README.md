# Data Science vs. Pump It Up Competition

## Blog

[Medium Blog](https://baotramduong.medium.com/data-science-vs-pump-it-up-competition-cccc8d58bb64 'Blog')

## Introduction

Tanzania, the largest country in East Africa, is suffering from a water crisis
* 4 million people lack access to an improved source of safe water
* 30 million people lack access to improved sanitation
* Water-borne illnesses, such as malaria and cholera, account for over half of the diseases affecting the population

Using data provided by The Tanzanian Water Ministry and Taarifa, DrivenData began a competition to solve this problem by building a classification system to predict whether a given water source is working correctly.
* 59,400 water points
* 40 features
* The given data included a target with three classes — ‘functional’, ‘non-functional’, and ‘functional needs repair’. 

The idea was to build a model that could predict if a given water-point would fall into one of these three classes. 

## PART I: EDA

### Data Source
      
            - https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/

<img src = '../main/Data/status_group_countplot.png' />

### Problems
* Sustainability: Regardless of hundreds of millions of dollars over budget and years past the original deadline of the Water Sector Development Program (WSDP), local government and communities find themselves unable to raise the money to fix and maintain their water points. 
* Power struggle: Full responsibility for operating, maintaining and sustaining water points is done at the village level. However, disbursement of funds and report of functionality must follow a long bureaucratic process all the way from the village, to the district, and, finally, to the Ministry of Water. The problem found is not only the miscommunication but also the power struggle around roles, responsibilities, and accountability between many different levels of government.

## PART IIA: Modelings

|FIELD1|Model                        |Accuracy|CV  |Precision|Recall|F1 Score|MAE |MSE |RMSE|AUC |Bias                |Variance           |
|------|-----------------------------|--------|----|---------|------|--------|----|----|----|----|--------------------|-------------------|
|0     |Decision Tree                |75.2    |0.72|0.64     |0.66  |0.65    |0.28|0.34|0.58|-   |0.03                |0.39               |
|1     |Logistic Regression          |65.27   |0.74|0.6      |0.67  |0.58    |0.42|0.55|0.74|0.82|0.24                |0.55               |
|2     |KNN                          |75.45   |0.72|0.64     |0.67  |0.65    |0.28|0.35|0.59|-   |0.05                |0.40               |
|3     |Bagged Tree                  |78.44   |0.76|0.68     |0.69  |0.68    |0.24|0.29|0.54|-   |0.01                |0.37               |
|4     |Random Forest                |79.24   |0.77|0.69     |0.69  |0.69    |0.23|0.28|0.53|-   |0.02                |0.36               |
|5     |Gradient Boost               |79.7    |0.78|0.69     |0.7   |0.69    |0.23|0.28|0.53|-   |0.03                |0.36               |
|6     |ADABoost                     |63.88   |0.72|0.57     |0.61  |0.56    |0.43|0.57|0.75|-   |0.21                |0.51               |
|7     |XGBoost                      |77.31   |0.78|0.67     |0.71  |0.68    |0.26|0.31|0.56|-   |0.08                |0.41               |
|8     |SVM                          |72.96   |0.76|0.64     |0.71  |0.65    |0.32|0.41|0.64|-   |0.16                |0.48               |

## PART IIB: Modelings without Correcting Class Imbalance

|FIELD1|Model                        |Accuracy|CV  |Precision|Recall|F1 Score|MAE |MSE |RMSE|AUC |Bias                |Variance           |
|------|-----------------------------|--------|----|---------|------|--------|----|----|----|----|--------------------|-------------------|
|0     |Imbalance Decision Tree      |75.96   |0.72|0.65     |0.66  |0.65    |0.27|0.32|0.57|-   |0.01                |0.36               |
|1     |Imbalance Logistic Regression|74.87   |0.74|0.68     |0.56  |0.58    |0.27|0.3 |0.55|0.81|0.01                |0.25               |
|2     |Imbalance KNN                |78.96   |0.73|0.7      |0.66  |0.68    |0.23|0.27|0.52|-   |0.01                |0.32               |
|3     |Imbalance Bagged Tree        |79.16   |0.76|0.69     |0.66  |0.67    |0.23|0.27|0.52|-   |-0.01               |0.32               |
|4     |Imbalance Random Forest      |80.37   |0.77|0.71     |0.67  |0.69    |0.22|0.26|0.51|-   |0.0                 |0.32               |
|5     |Imbalance Gradient Boost     |81.3    |0.78|0.73     |0.68  |0.7     |0.2 |0.24|0.49|-   |0.0                 |0.31               |
|6     |Imbalance ADABoost           |71.8    |0.72|0.6      |0.51  |0.5     |0.3 |0.32|0.57|-   |0.02                |0.22               |
|7     |Imbalance XGBoost            |80.34   |0.78|0.76     |0.63  |0.66    |0.21|0.24|0.49|-   |0.0                 |0.27               |
|8     |Imbalance SVM                |78.54   |0.76|0.75     |0.6   |0.63    |0.23|0.26|0.51|-   |0.02                |0.25               |

##  Summary of Key Findings

### Feature Importance

<img src = '../main/Data/decision_tree_clf_feature_importances.png' />

### Best Model: Grandient Boost (without SMOTE)

<img src = '../main/Data/GradientBoostingClassifier Result.png' />

<img src = '../main/Data/confusion_matrix.png' />

* The highest accuracy score is 81.30%. 
* Here we see that Train accuracy of 99.33% versus Test accuracy of 81.30% have a big discrepancy, meaning the model is highly overfit. 
* The model does very well in classifying functional (1) as function (1) and non-functional (0) as non-functional (0). 
* However it doesn’t do as well when classifying functional-needs-repair (2), it tends to classify it as functional (1) more than non-functional (0). Classifying functional-needs-repair as functional (1) is more costly than classifying it as non-functional (0) because repair and maintenance will be overdue, causing more damages, leads to non-functional. 
* We can also see that here with  f1 (which is average of the  precision and recall) score are significantly lower for class 2.

### Compared with Grandient Boost with SMOTE

<img src = '../main/Data/GradientBoostingClassifier Result (withSMOTE).png' />

<img src = '../main/Data/confusion_matrix withSMOTE.png' />

When compare the imbalanced and balanced models, we see that the Imbalanced model has a higher accuracy overall but we lower accuracy for class 2, which is only 295 correctly classified. For the Balance model, class 2 are classified correctly classified 374 times but we sacrifice accuracy overall. 

##  Summary of Actionable Insights
1. Focus on sustainability: early preventative strategy rather than letting things go broken
2. Decentralized management: we need to restructure authority so that there is a system of co-responsibility between the central, regional and local levels. 
3. Improved payment system: 
* A local payment system should be put in place so that the user-group can be independently responsible for their own water points
* Direct funding from international donors to village-level should also be implemented instead of having to go through the long bureaucratic process where money get lost along the way between ministry and district level.

##  Future Works
1. Since correcting class imbalance did not improve the model, we can try model stacking i.e build a binary classification between functional vs non-functional and another binary classification between functional vs. functional needs repair.
2. Try more parameters tuning with more and wider range of options
3. Work to reduce overfit while maintaining and/or improving accuracy score

## Reference
DrivenData. (n.d.). Pump it Up: Data Mining the Water Table. Retrieved from https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/

Jiménez, A., & Pérez-Foguet, A. (2011). The relationship between technology and functionality of rural water points: evidence from Tanzania. Water science and technology : a journal of the International Association on Water Pollution Research, 63(5), 948–955. https://doi.org/10.2166/wst.2011.274

Lemmens, R., Lungo, J., Georgiadou, Y., & Verplanke, J. (2017). Monitoring Rural Water Points in Tanzania with Mobile Phones: The Evolution of the SEMA App. ISPRS International Journal of Geo-Information, 6(10), 316. doi:10.3390/ijgi6100316

Mithrakumar, M. (2019, November 12). How to tune a decision tree? Retrieved March 29, 2021, from https://towardsdatascience.com/how-to-tune-a-decision-tree-f03721801680

Nelson, D. (n.d.). Gradient boosting classifiers in Python with scikit-learn. Retrieved March 23, 2021, from https://stackabuse.com/gradient-boosting-classifiers-in-python-with-scikit-learn/

Shore, R. (n.d.). Water In Crisis — Spotlight Tanzania. The Water Project. Retrieved February 28, 2021, from https://thewaterproject.org/water-crisis/water-in-crisis-tanzania

The Water Project. (n.d.). Facts and Statistics about Water and Its Effects. The Water Project. Retrieved February 28, 2021, from https://thewaterproject.org/water-scarcity/water_stats
water.org. (n.d.). Tanzania’s Water Crisis — Tanzania’s Water In 2020. Water.Org. Retrieved February 28, 2021, from https://water.org/our-impact/where-we-work/tanzania/
