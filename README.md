# README 
## Capstone
### Contents:
- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Data Import and Cleaning](#Data-Import-and-Cleaning)
- [Preliminary EDA](#Preliminary-EDA)
- [Feature Engineering](#Feature-Engineering)
- [Model Interpretation](#Model-Interpretation)
- [Results](#Results)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)

### Problem Statement
Given the rise of Peer to Peer (P2P) lending, is it possible to predict which loans are at risk of defaulting or incomplete payback? Using Lending Club's P2P data, I will build a model to classify existing loans as Success or Failure based on their attributes.

### Executive Summary 
Financial data is one of the fastest growing 

### Data Import and Cleaning
Due to the limited time scope for this project, I opted to utilize a dataset that was provided to the Kaggle community by a generous fellow data scientist. Although they started the process by removing some symbols and converting two features to the correct format, many opportunities for cleaning the data persisted. 


### Preliminary EDA


### Feature Engineering
For this project I engaged in three separate types of Feature Engineering: Ordinal rankings, One-Hot (dummy) encoding, and Interaction Features. 

Ordinal rankings were required for features such as the loan grades provided by Lending Club and also the length of employment reported. 

Dummy variables were created for features in which they had either binary or multiple values and included purpose, verification_status, addr_state, pymnt_plan, initial_list_status, application_type, hardship_flag, disbursement_method, debt_settlement_flag. This resulted in an addition of 65 columns. 

Interaction Features were the final category of feature engineering, as a way of dealing with the autocorrelation present in some of the features that were very similar in function, where the originals were then dropped. This resulted in an addition of 19 columns. 

Additionally, there was text present that was inputed by the loan applicants. This resulted in a massive range of text values for the following three categories: emp_title, title, and desc. As a way of dealing with this, I took the lengths of these three features and created new columns with their lengths. Further, I added the text strings together via concatenation in case I wanted to do CountVectorization, although I didn't get there in this attempt. I also took the length of the combination of three features to get a new, comprehensive length.


### Model Interpretation
In approaching this problem, I used three separate classification models: Logistic Regression, Random Forest and XGBoost. Each of the models had their merits, but the overwhelming success came entirely from XGBoost with results that vastly outperformed in comparison to Logistic Regression and Random Forest.

#### Results:
Logistic Regression
    Accuracy score: 78.92%
    Recall score: 99.91%
    Precision score: 78.91%
    Specificity score: 1.36%
    F1 score: 88.18%

Random Forest
    Accuracy score: 91.72%
    Recall score: 100.00%
    Precision score: 90.48%
    Specificity score: 61.13%
    F1 score: 95.0%

XGBoost
    Accuracy score: 97.75%
    Recall score: 98.68%
    Precision score: 98.46%
    Specificity score: 94.32%
    F1 score: 98.57%

### Conclusions and Recommendations



