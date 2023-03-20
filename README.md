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
The goal of this project are:
1. Prediction of the results of the marketing campaign for each customer and clarification of factors which affect the campaign results. This helps to find out the ways how to make marketing campaigns more efficient.
2. Finding out customer segments, using data for customers, who subscribed to term deposit. This helps to identify the profile of a customer, who is more likely to acquire the product and develop more targeted marketing campaigns.

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
11. day: last contact day of the month (numeric: 1-31)
12. duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.

*Other attributes:*

13. campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
14. pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; -1 means client was not previously
contacted)
15. previous: number of contacts performed before this campaign and for this client (numeric)
16. poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')

**Output variable (desired target):**

17. y - has the client subscribed a term deposit? (binary: 'yes','no')

## 4. Data Wrangling
[Data Wrangling Notebook](https://github.com/tw1107/Springboard-Capstone-Bank-Marketing/blob/main/notebook/01_Data_Wrangling.ipynb)

Major steps:
1. The dataset has a shape of (11162, 17)
2. Check for duplicates:  There are 0 duplicates for this dataset
3. Check for missing values: There are 0 missing values
4. Will perform EDA and see if we need to drop any fields for pre processing

## 5. EDA
[EDA Notebook](https://github.com/tw1107/Springboard-Capstone-Bank-Marketing/blob/main/notebook/02_EDA.ipynb)

**Term Deposit** is what we are predicting, EDA is all related to deposit (our target feature). Summary: 

![alt text](https://github.com/tw1107/Springboard-Capstone-Bank-Marketing/blob/main/images/Screenshot%202023-03-19%20at%205.43.19%20PM.png)
- Target variable 'deposit' is balanced, we can use accuracy as a metric for a model, which predicts the campaign outcome.

**Cliet Demographic Analysis** 

![alt text](https://github.com/tw1107/Springboard-Capstone-Bank-Marketing/blob/main/images/Demographic.png)
1. 36% of clients are in the age 30's-40's
2. Top 3 job: 20% of clients work in mamangement, followed by 16% in blue-collar, and 15% technician.
3. More than half with 52% are married
4. 45% have a secondary education
5. Mostly have no loan and no default credit card.
6. It's 50-50 in terms of having housing
7. 90% of clients have balance below $20,000

**Campaign Analysis** 

![alt text](https://github.com/tw1107/Springboard-Capstone-Bank-Marketing/blob/main/images/Screenshot%202023-03-19%20at%205.46.20%20PM.png)
1. Some numerical features have outliers (especially 'pdays', 'campaign' and 'previous' columns), will imput the ourlers by mean for pre-processing.
2. Conctact by celler have 39% deposit rate
3. May & August have higher deposit rate
4. Unknown outcome of the previous marketing campaign has higher depost rate

## 6. Feature Engineer & Modeling
[Feature engineering & ML Notebook](https://github.com/tw1107/Springboard-Capston-House-Price/blob/main/notebook/04_Modeling.ipynb)

**Feature Engineering Major Steps:**
1. Encode some categorical features as ordered numbers when there is information in the order
2. Log transform of the skewed numerical features to lessen impact of outliers
3. Transformation of categorical features vis one-hot encoding
4. Split into testing and training datasets
5. Standardize the magnitude of numeric features using a scaler

**Modeling Major Steps:** 
Created below models with RandomizedSearchCV hyperparameter tuning for model optimization
1. Customer Segmentation Clustering
2. 

Model Validation Metric:
1. RMSE
2. R Squared

![Model Performance Score](https://github.com/tw1107/Springboard-Capston-House-Price/blob/main/images/Screenshot%202023-02-26%20at%202.35.43%20PM.png)

## 7. Future improvements
