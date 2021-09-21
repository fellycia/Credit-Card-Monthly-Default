# Credit-Card-Monthly-Default
To view all the plots, click here (as github performs a static render of the notebooks only): 
https://nbviewer.jupyter.org/github/fellycia/Credit-Card-Monthly-Default/blob/main/Monthly%20Credit%20Card%20Default.ipynb

## Background
A well-established bank in Asia Pacific is looking to use data to better their nonperforming loan ratio.
Nonperforming loan ratio is the amount of nonperforming loans to the total amount of outstanding loans the bank holds.
## Problem Statement
The bank wants to predict whether a loan will be payed back to the bank or not. At the moment, the bank if fully dependent on the credit risk rating and their past experience. However, the bank is unable to accurately predict whether a client is able to pay their loan back on a continuous month to month.

Using [Default of Credit Card Clients Dataset](https://www.kaggle.com/uciml/default-of-credit-card-clients-dataset), which contains information on default payments, demographic factors, credit data, history of payment, and bill statements of credit card clients in Taiwan from April 2005 to September 2005, the aim is to predict the risk of a client defaulting on a monthly installment and how much a client can pay in any given period.

## Executive Summary
When doing exploratory data analysis, we found that:

- Although there are more females than males with credit cards, there is higher chance of defaulting if a client is a male.
- There is a general trend that the chances of defaulting increases as age increase.
- Although most credit cards holder are single, the highest percentage of defaults came from others, followed by married and single.
- Although most credit card holders have university and graduate school degree, the highest percentage of defaults came from clients with high school degree.
- As the credit limit increases, the percentage of clients defaulting decreases.
- Defaults seem to occur mostly when clients had a payment delay for more than 2 months.

For modeling:
We will use classifiers (Logistic Regression, Random Forest, XGBoost) to predict if a client is able to pay the installment in any given month and the risk of a client defaulting. We will then use regression (Linear Regression, Random Forest Regressor) to predict how much a client may be able to pay in any given period.
As we are interested in both positive and negative classes. Hence, we will be using ROC AUC as our metric for classification, root mean squared error (RMSE) for regression so as to penalize large errors.

XGBoost proved to be the best classification model to separate defaulters and non defaulters. It attained the highest test ROC AUC score of 77% in separating the classes. Some of the top important features in determining if a client would default or not are repayment statuses and credit card limit amount.

Random forest regressor is the best model to predict how much a client can pay, with the lowest root mean squared error of 130 on test data. The predictions and actual y values are close to one another, indicating a good prediction.

As the models perform relatively well on unseen data, banks can start to predict monthly if a client will default and serve their clients better to reduce their chances of defaulting.

## Data Dictionary
| Feature              | Type     | Description                                                                                        |
|:----------------------|:----------|:----------------------------------------------------------------------------------------------------|
| ID            | int      | ID of each client                                                                                  |
| LIMIT_BAL             | float      | Amount of given credit in NT dollars (includes individual and family/supplementary credit)                                                                           |
| SEX            | int      | Gender (1=male, 2=female)                                                                         |
| EDUCATION              | int      | (1=graduate school, 2=university, 3=high school, 4=others, 5=unknown, 6=unknown)                                                                         |
| MARRIAGE                | int      | Marital status (1=married, 2=single, 3=others)                                                                  |
| AGE        | int      | Age in years                                              |
|PAY_0 | int      | Repayment status in September, 2005 (-1=pay duly, 1=payment delay for one month, 2=payment delay for two months, … 8=payment delay for eight months, 9=payment delay for nine months and above)                                                                                        |
| PAY_2                   | int | Repayment status in August, 2005 (scale same as above)                                                      |
| PAY_3         | int      | Repayment status in July, 2005 (scale same as above)                                                                       |
| PAY_4            | int | Repayment status in June, 2005 (scale same as above)                                                                    |
| PAY_5           | int      | Repayment status in May, 2005 (scale same as above) |
| PAY_6              | int      | Repayment status in April, 2005 (scale same as above)                                                      |
| BILL_AMT1               | float      | Amount of bill statement in September, 2005 (NT dollar)                                                      |
| BILL_AMT2              | float      |Amount of bill statement in August, 2005 (NT dollar)                                                     |
| BILL_AMT3              | float      | Amount of bill statement in July, 2005 (NT dollar)                                                      |
| BILL_AMT4               | float      | Amount of bill statement in June, 2005 (NT dollar)                                                      |
| BILL_AMT5               | float      | Amount of bill statement in May, 2005 (NT dollar)                                                      |
| BILL_AMT6               | float      | Amount of bill statement in April, 2005 (NT dollar)                                                      |
| PAY_AMT1               | float      | Amount of previous payment in September, 2005 (NT dollar)                                                      |
| PAY_AMT2               | float      | Amount of previous payment in August, 2005 (NT dollar)                                                      |
| PAY_AMT3               | float      | Amount of previous payment in July, 2005 (NT dollar)                                                      |
| PAY_AMT4               | float      | Amount of previous payment in June, 2005 (NT dollar)                                                      |
| PAY_AMT5              | float      | Amount of previous payment in May, 2005 (NT dollar)                                                      |
| PAY_AMT6              | float      | Amount of previous payment in April, 2005 (NT dollar)                                                      |
| default.payment.next.month              | int      | Default payment (1=yes, 0=no)                                                      |
