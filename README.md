# Credit-card-fraud-detection

## About
Credit card fraud occurs when unauthorized individuals or entities use someone else's credit card information to make purchases or access funds. As credit card transactions become increasingly digital, fraud detection systems need to handle large volumes of data in real-time while minimizing false positives (legitimate transactions incorrectly flagged as fraud). Machine learning (ML) is an effective tool for fraud detection, as it can analyze transaction patterns and detect anomalies that may indicate fraudulent activity. The goal of using ML is to build a model that can classify transactions as either legitimate or fraudulent based on transaction characteristics and historical data.

## Problem Definition

## Data Preprocessing
1. Data Collection
Credit Card Fraudalent Dataset : https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

Data Overview 
- Time: Timestamp of the transaction.
- Amount: The amount of money involved in the transaction.
- Features V1 to V28: These are anonymized features derived from PCA transformations of the original data for privacy reasons.
- Class: The label indicating whether the transaction is fraudulent (1) or legitimate (0).

2. Data Exploration

Data description
- All of the data are numerical, no categorical or text based column
- There are 31 columns 284000 records
- The features are expressed at the transaction level, they are not agregated at the user level
- The features are derived from PCA transformation (an effective approach for reducing the dimensionality of the data) which mean tha data set was likely a lot wider. In short it removes the interpretability aspect
- There are 284315 legitimate record and 492 confirmed fraudalent record
- This dataset represent supervised learning problem (binary (yes/no) classification)

3. Sampling from imbalance data
While balancing the data helps increase recall, it might also increase false positives (incorrectly labeling a legitimate transaction as fraud), which can be costly in a real-world application. For example, false positives can result in customer dissatisfaction, delays, and increased operational costs. In certain cases, focusing only on the minority class (fraudulent transactions) could lead to a situation where too many legitimate transactions are incorrectly flagged as fraud.

4. Training Supervised Learning Model
   
Model Train : Baseline Logistic Regression using scikit-learn
 - Confusion Matrix = The model has a high true positive and true negative while on the other side has low false positive and false negative. Therefore this mean the model perform quite well from this perspective. However the false negative should better be lower. 

Improving Logistic Regression Model through Hyperparameter Selection
- Hyper parameter = class_weight adjusted to {0:1, 1:50}

 Logistic Regression Model interpretation :
 


5. Performance Metrics for Fraud Detection

6. Optimal Model Selection

7. Improving Model Performance 

Interpreting the Logistic Regression Model 


