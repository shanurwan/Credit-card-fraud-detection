# Credit-card-fraud-detection

## About
Credit card fraud occurs when unauthorized individuals or entities use someone else's credit card information to make purchases or access funds. As credit card transactions become increasingly digital, fraud detection systems need to handle large volumes of data in real-time while minimizing false positives (legitimate transactions incorrectly flagged as fraud). Machine learning (ML) is an effective tool for fraud detection, as it can analyze transaction patterns and detect anomalies that may indicate fraudulent activity. The goal of using ML is to build a model that can classify transactions as either legitimate or fraudulent based on transaction characteristics and historical data.

## Methodology
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
   
While balancing the data helps increase recall, it might also increase false positives (incorrectly labeling a legitimate transaction as fraud), which can be costly in a real-world application. For example, false positives can result in customer dissatisfaction, delays, and increased operational costs. In certain cases, focusing only on the minority class (fraudulent transactions) could lead to a situation where too many legitimate transactions are incorrectly flagged as fraud. Therefore instead of balancing the data, class weight adjustmen was implemented. 

4. Training Supervised Learning Model
   
Model Train : Baseline Logistic Regression 
 - Logistic Regression is often used as a starting point to benchmark more complex models.
 - Confusion Matrix = The model has a high true positive and true negative while on the other side has low false positive and false negative. Therefore this mean the model perform quite well from this perspective. However the false negative should better be lower. 

Improving Logistic Regression Model through Hyperparameter Selection
- Hyperparameter = class_weight adjusted to {0:1, 1:50}

Model Train : Baseline Logistic XGBoost Classifier
- XGBoost (Extreme Gradient Boosting) is one of the most popular machine learning algorithms, especially in applications like fraud detection. It is known for its high accuracy, speed, and flexibility.
- Confusion Matrix = The model produce a significantly higher true positive and true negative while on the other side has lower false positive and false negative compare to previous model. This indicate better performance from this perspective. However there are 9 case of fraudalent unable to be detected which potentially can be improved.

Improving XGBoost Model through Hyperparameter Selection
- Hyperparametr = scale_pos_weight adjusted to 100

5. Performance Metrics for Fraud Detection
 - Estimate cost of fraud
 - Classification Report

6. Improving Model Performance 
- Up-sampling the Minority Class with SMOTE

## Finding and Recommendation
1. XGBoost as an Optimal Model for Fraud Detection:
XGBoost is a highly effective choice for fraud detection due to its ability to handle imbalanced data, capture complex patterns, and deliver high accuracy. With its strengths in interpretability, scalability, and speed, it is particularly well-suited for real-time fraud detection systems where both model accuracy and quick decision-making are critical. Its ability to deal with non-linear relationships and interactions between features makes it particularly useful for identifying fraudulent patterns that might not be easily detected by simpler models.
Cost Comparison:

2. The estimated cost for implementing the XGBoost model is $29,426, which is cheaper compared to Logistic Regression at $30,020. Although the cost difference is relatively small, XGBoost offers better performance (in terms of precision, recall, and F1-score) and may lead to more cost-effective fraud detection solutions over time due to its ability to handle more complex patterns and provide higher accuracy.

3. Model Performance:
The XGBoost model performed well with:
Precision: 93% — This indicates that 93% of the transactions predicted as fraudulent are actually fraudulent, minimizing false positives.
Recall: 88% — This shows that 88% of actual fraudulent transactions were correctly identified, minimizing false negatives.
F1-Score: 90% — The F1-score, which balances precision and recall, reflects a strong overall performance in detecting fraud without sacrificing one metric for the other.
This high performance is crucial for fraud detection, where both precision (to avoid false alarms) and recall (to catch as many fraudulent transactions as possible) are critical.

4. Feature Importance:
In both models (XGBoost and Logistic Regression), the feature V14 was identified as the most important feature in XGBoost and second highest in Logistic Regression. This indicates that V14 plays a critical role in predicting fraudulent transactions. The high importance of this feature in both models suggests that it carries significant information regarding transaction behavior and should be further examined or prioritized for feature engineering and model optimization.

5. Recommendation for Future Steps:
   
Fine-Tune XGBoost Model: Given the strong performance of XGBoost, further hyperparameter tuning and cross-validation should be performed to optimize the model’s parameters and ensure even higher accuracy and robustness across different datasets and real-world scenarios.

Monitor Overfitting: Regular monitoring should be conducted to ensure that the model is not overfitting to the training data. While XGBoost generally has built-in regularization to prevent this, it's important to regularly evaluate performance on out-of-sample data.

Feature Engineering: Since V14 is a key feature, further exploration of its relationship with other features could provide insights into more complex interactions. Additionally, introducing new features or enhancing existing ones could improve model performance.

Cost-Benefit Analysis: While XGBoost is slightly cheaper to implement, it is recommended to conduct a cost-benefit analysis based on the real-world impact of fraud detection performance. If Logistic Regression performs sufficiently well for the given use case (with acceptable precision, recall, and F1), it may still be a viable option for cost-sensitive environments, especially if interpretability is a primary concern.

Real-Time Monitoring: For fraud detection systems, real-time model deployment is essential. XGBoost’s speed and efficiency should be leveraged for real-time prediction and continuous monitoring of transactions to ensure immediate flagging of potential fraud.
