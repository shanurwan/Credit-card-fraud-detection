# Credit-card-fraud-detection

## About
Credit card fraud occurs when unauthorized individuals or entities use someone else's credit card information to make purchases or access funds. As credit card transactions become increasingly digital, fraud detection systems need to handle large volumes of data in real-time while minimizing false positives (legitimate transactions incorrectly flagged as fraud). Machine learning (ML) is an effective tool for fraud detection, as it can analyze transaction patterns and detect anomalies that may indicate fraudulent activity. The goal of using ML is to build a model that can classify transactions as either legitimate or fraudulent based on transaction characteristics and historical data.

## Problem Definition

## Data Preprocessing
1. Data Collection
Credit Card Fraudalent Dataset : https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

Data Overview 
Time: Timestamp of the transaction.
Amount: The amount of money involved in the transaction.
Features V1 to V28: These are anonymized features derived from PCA transformations of the original data for privacy reasons.
Class: The label indicating whether the transaction is fraudulent (1) or legitimate (0).

2. Data Exploration

Data description
- All of the data are numerical, no categorical or text based column
- There are 31 columns 284000 records
- The features are expressed at the transaction level, they are not agregated at the user level
- The features are derived from PCA transformation (an effective approach for reducing the dimensionality of the data) which mean tha data set was likely a lot wider. In short it removes the interpretability aspect

Managing labels in a fraud detection context
- There are 284315 legitimate record and 492 confirmed fraudalent record

3. Data Balancing 
