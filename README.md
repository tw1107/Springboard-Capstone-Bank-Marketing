![alt text](https://github.com/tw1107/Springboard-Capstone-Bank-Marketing/blob/main/images/dataset-cover.jpg)

# Bank Marketing Campaign: Predicting Term Deposit Subscriptions
Marketing campaigns are characterized by focusing on the customer needs and their overall satisfaction. 
Nevertheless, there are different variables that determine whether a marketing campaign will be successful or not. 
There are certain variables that we need to take into consideration when making a marketing campaign.

What is a Term Deposit?
A Term deposit is a deposit that a bank or a financial institurion offers with a fixed rate (often better than just opening deposit account) in which your money will be returned back at a specific maturity time. For more information with regards to Term Deposits please click on this link from Investopedia:

## 1. Problem Statement
How can the financial institution have a greater effectiveness for future marketing campaigns?

## 2. Goal
The goal of this project is to analyze the bank's most recent marketing campaign and identify patterns that will help the financial institution improve for future campaigns. 
This analysis will enable the bank to have greater effectiveness in future marketing campaigns.

## 3. Data
Marketing bank dataset uploaded originally in the UCI Machine Learning Repository. 
The dataset gives information about a marketing campaign of a financial institution in which we will have to analyze in order to find ways to look for future strategies in order to improve future marketing campaigns for the bank.

***Attribute Description:*** 

**Input Variables:**

*Bank client data:*
1. age: (numeric)
2. job: type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-emplo yed','services','student','technician','unemployed','unknown')
3. marital: marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)
4. education: (categorical: primary, secondary, tertiary and unknown)
5. default: has credit in default? (categorical: 'no','yes','unknown')
6. housing: has housing loan? (categorical: 'no','yes','unknown')
7. loan: has personal loan? (categorical: 'no','yes','unknown')
8. balance: Balance of the individual.

*Related with the last contact of the current campaign:*

9. contact: contact communication type (categorical: 'cellular','telephone')
10. month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')
11. day: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')
12. duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.

*Other attributes:*

13. campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
14. pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously
contacted)
15. previous: number of contacts performed before this campaign and for this client (numeric)
16. poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')

**Output variable (desired target):**

17. y - has the client subscribed a term deposit? (binary: 'yes','no')


## 4. Data Cleaning
[Data Cleaning Notebook](https://github.com/tw1107/Springboard-Capston-House-Price/blob/main/notebook/01_data_wrangling.ipynb)

Major steps:
1. Check for duplicates:  There are 0 duplicates for this dataset
2. Impute missing values
3. Transform numerical features to categorical when they are true catrgorical
4. Encode some categorical features as ordered numbers when there is information in the order

## 5. EDA
[EDA Notebook](https://github.com/tw1107/Springboard-Capston-House-Price/blob/main/notebook/02_EDA.ipynb)

**Sale Price** is what we are predicting, EDA is all related to SalePrice (our target feature). Below are some take away:

**Price of properties in Ames, Iowa** 
![alt text](https://github.com/tw1107/Springboard-Capston-House-Price/blob/main/images/Screenshot%202023-02-26%20at%201.53.12%20PM.png)

1. Average house sale price is around $180,000 in Ames.
2. There are a few properties over $500,000, but majority of houses are priced under $214,000.
3. The target variable is right skewed (positive skewness) and shows peakedness. As (linear) models fits better on normally distributed data, we require proper transformation. 

**The most important numeric predictors** 
![alt text](https://github.com/tw1107/Springboard-Capston-House-Price/blob/main/images/top10.png)

**Attributes most correlated with sale price** 
![alt text](https://github.com/tw1107/Springboard-Capston-House-Price/blob/main/images/Screenshot%202023-02-26%20at%202.12.07%20PM.png)

**Time vs Sale price** 
![alt text](https://github.com/tw1107/Springboard-Capston-House-Price/blob/main/images/year.png)

## 6. Feature Engineer & Modeling
[Feature engineering & ML Notebook](https://github.com/tw1107/Springboard-Capston-House-Price/blob/main/notebook/04_Modeling.ipynb)

**Feature Engineering Major Steps:**
1. Encode some categorical features as ordered numbers when there is information in the order
2. Create new features
3. Log transform of the skewed numerical features to lessen impact of outliers
4. Transformation of categorical features vis one-hot encoding
5. Split into testing and training datasets
6. Standardize the magnitude of numeric features using a scaler

**Modeling Major Steps:** 
Created below models with RandomizedSearchCV hyperparameter tuning for model optimization
1. Ridge 
2. Lasso 
3. ElasticNet
4. XGBoost
5. Gradient Boosting Regression
6. Light GBM
7. Stacking Model with ElasticNet as the meta_mode

Model Validation Metric:
1. RMSE
2. R Squared

![Model Performance Score](https://github.com/tw1107/Springboard-Capston-House-Price/blob/main/images/Screenshot%202023-02-26%20at%202.35.43%20PM.png)

## 7. Future improvements
