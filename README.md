# Predicting Success or Failure with Lending Club Loan Data 
## Contents:
- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Data Import and Cleaning](#Data-Import-and-Cleaning)
- [Preliminary EDA](#Preliminary-EDA)
- [Feature Engineering](#Feature-Engineering)
- [Model Interpretation](#Model-Interpretation)
- [Results](#Results)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)

## Problem Statement
Using Machine Learning, is it possible to predict which loans are at risk of defaulting or incomplete payback? To answer this question I build classification models that take Lending Club's loan data as input.

## Executive Summary 
As the internet develops into a mature institution, our interactions mature as well. Where it was once unfathomable to enter our personal financial information onto websites, we are now living the majority of our financial lives online. As we have acclimated to the uncertainty present in dealing with strangers online, a new form of a classic debt vehicle grow in popularity: online peer-to-peer lending. Whereas lending to friends, family and businesses has always existed, the acceptance of the Internet in our daily lives allows much easier access to capital.

As individual borrowers connect to these online lending platforms, their information is processed and turned into investment opportunity for lenders. One such platform is Lending Club, founded in 2007 with the pitch involving an algorithm that would match borrowers and lenders with similar interests. The theory behind the algorithm was that people with similar interests would have a social contract that lowered the risk of default. Not surprisingly, when the company went public in 2014 they were forced to remove this feature as well as no longer state that borrowers were less likely to default on these loans.

These loan applications create wide ranges of risk profiles for investors to participate in, however with the large quantities of potential lenders it is important for would-be creditors to quickly and accurately determine the viability of loans. Keeping this need in mind, I look to machine learning to create classification models that accomplish those needs. 

In the notebooks, it is important to engage with them in the order they are labeled: first opening and running "EDA (1 of 3)", then "Feature Engineering (2 of 3)" and finally "Modeling (3 of 3)".

## Data Import and Cleaning
Due to the limited time scope for this project, I opted to utilize a dataset that was provided to the Kaggle community by a generous fellow data scientist - https://www.kaggle.com/wordsforthewise/lending-club. Although they started the process by removing some symbols and converting two features to the correct format, many opportunities for cleaning the data persisted. 


## Preliminary EDA
While conducting preliminary exploratory data analysis I found that there were a large quantity of missing values at approximately 108.5 Million missing values. This represents approximately a third of the 345 Million values, so I deal with this problem in a way that does not involve imputing fake numbers.


## Feature Engineering
For this project I engaged in three separate types of Feature Engineering: Ordinal rankings, One-Hot (dummy) encoding, and Interaction Features. 

Ordinal rankings were required for features such as the loan grades provided by Lending Club and also the length of employment reported. 

Dummy variables were created for features in which they had either binary or multiple values and included purpose, verification_status, addr_state, pymnt_plan, initial_list_status, application_type, hardship_flag, disbursement_method, debt_settlement_flag. This resulted in an addition of 65 columns. 

Interaction Features were the final category of feature engineering, as a way of dealing with the autocorrelation present in some of the features that were very similar in function, where the originals were then dropped. This resulted in an addition of 19 columns. 

Additionally, there was text present that was inputed by the loan applicants. This resulted in a massive range of text values for the following three categories: emp_title, title, and desc. As a way of dealing with this, I took the lengths of these three features and created new columns with their lengths. Further, I added the text strings together via concatenation in case I wanted to do CountVectorization, although I didn't get there in this attempt. I also took the length of the combination of three features to get a new, comprehensive length.


## Model Interpretation
In approaching this problem, I used three separate classification models: Logistic Regression, Random Forest and XGBoost. Each of the models had their merits, but the overwhelming success came entirely from XGBoost with results that vastly outperformed in comparison to Logistic Regression and Random Forest. Results are below!


### Results:
Logistic Regression:
    
    - Accuracy score: 78.92%
    
    - Recall score: 99.91%
    
    - Precision score: 78.91%
    
    - Specificity score: 1.36%

    - F1 score: 88.18%

Random Forest:

    - Accuracy score: 91.72%

    - Recall score: 100.00%

    - Precision score: 90.48%
    
    - Specificity score: 61.13%
    
    - F1 score: 95.0%

XGBoost:

    - Accuracy score: 97.75%
    
    - Recall score: 98.68%
    
    - Precision score: 98.46%
    
    - Specificity score: 94.32%
    
    - F1 score: 98.57%


## Conclusions and Recommendations

Throughout this process, I show that it is indeed possible to make accurate predictions regarding the quality of a loan as defined by Success or Failure. Out of the models tested, XGBoost is the clear choice for this, as it improves in all metrics (with the exception of Recall and Fit). 

For future implementations of this project, I recommend looking into further analysis of the textual elements via Natural Language Processing. Specifically, I would like to incorporate CountVectorizer into this model in order to utilize the raw text input as Chang et al did, rather than just measuring the length of the text provided for each of the three features. 

Additional feature engineering is also available for Zip code data, as it was not feasible to bring in additional data sets and join them in order to create mean and median incomes as Li & Han did.

In these models, I focused exclusively on binary classification problems. In reality, there are more than two classifications that exist for loans. In order to comprehensively cover these ranges of outcomes it would be ideal to transform this problem from a binary to multinomial classification. 

The size of the data caused the optimization process to be slowed dramatically, and drastically reduced my ability to perform GridSearch on models. To solve this issue it would be ideal if there was a small development set created in order to quickly and accurately fine tune the parameters to achieve optimization without having to subject the entire dataset to the process.
