# Kaggle_Compeition

## 1. Media Cost Prediction: 
The train and public 20% test set is in the Kaggle: [Tabular Regression with a Media Campaign Cost](https://www.kaggle.com/competitions/playground-series-s3e11). The best score we got was 0.29698 RMSLE in the private ranking for the whole test set. We provide our experiment overview and the simplified final code here. 

### Workflow
  * Cleaning Phase:
       #### 1. Outlier Removal:
    **1.5 IQR:** Too many outliers are detected from IQR, even increased the coefficient to 3. 

    **95% CI:** Get the reasonable range of outliers. 

    **Outlier detection algorithms:** One-Class SVM > Elliptic Envelope > Isolation Forest 

**Note:** One-Class SVM is a proper option. Although we choose it to generate a new dataset without outliers, the final performance is slightly worse than the original dataset with outliers. 

   * Transformation & Dimensionality Reduction:

     #### 1. Standardization:
     #### 2. Box-Cox/Yeo-Johnson: Good for our highly skewness features, but may not valid for negative values. 
     #### 3. Dimensionality Reduction:
     **PCA or tSNE** 

**Note:** Standardization makes our prediction worse for our machine learning methods, but it is necessary for deep learning networks. Box-Cox/Yeo-Johnson is invalid for our sets. PCA is a better option here. 

  * Further Feature Engineering:
     #### 1. Feature Selection
     #### 2. Feature Construction
     #### 3. Feature Concatenation

**Note:** Droping less significant features and construct more meaningful new features are really good. Extra concatenation from new features has unstable performance. 

   * Modelling Phase:
     #### 1. Basic Machine Learning Models: 
     #### 2. Ensemble Models: 
     **Voting:** Decision Tree + Random Forest

     **Boosting:** AdaBoost, XGBoost, LightGBoost. 
     #### 3. Deep Learning: Simple Fully-Connected Layers. 