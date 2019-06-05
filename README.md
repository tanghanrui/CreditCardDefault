# Predict Credit Card Payment Default

## INTRODUCTION
The credit card issuer in Taiwan faced an increasing default crisis since 2006. They over-issued credit cards to unqualified applications in order to expand the market share. This project will use credit card datasets from 2000 to 2003 to find out key drivers of payment default and improve credit card scoring system to better predict customers’ likelihood of default. 

## ABOUT THE DATA
1.	Source: https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients
2.	Time period: Jan 2000 to Dec 2003
3.	Total observations: 300000
4.	Number of Features: 23
5.	Outcome Feature:  default_next_month

## Feature Description
default_payment_next_month: Will the customer default next month (Yes = 1, No = 0)?

limit_bal: Household credit limit

sex:	1 = male; 2 = female

education	1 = graduate school; 2 = university; 3 = high school; 4 = others

marriage	1 = married; 2 = single; 3 = divorced, 0 = others

age	years

pay_april through pay_sept	Payment status from the previous 6 months (April - Sept. 2006). -2: No consumption; -1: Paid in full; 0: The
use of revolving credit; 1 = payment delay for one month; 2 = payment delay for two months; . . .; 8 = payment delay for eight months; 9 = payment delay for nine months and above. 

bill_april through bill_sept	Bill statement amount from the previous 6 months (April - Sept. 2006).

pay_amt_april through pay_amt_sept	Previous payment amount from the previous 6 months (April - Sept. 2006)

## METHOD AND VARIABLE SELECTION
I first conducted a brief exploratory analysis and found correlation between whether the cardholders will default next month and sex, bill amount in September, marriage, and credit limit. After analyzing these features (please see figure 5 to 8), I summarized:
1.	Cardholders with high credit limit have lower chance of default
2.	Men have higher risk of default than women
3.	People who married have higher chance of default than those are singles
4.	Defaulters tend to have a slightly lower bill amount in September

## Pre-processing
The dataset is quite clean as there are no near zero variables or missing values. 

## Variable and model selection
I made hypotheses that cardholders who always paid off their statement balance will pay the bill next month. I created a new feature call “fullpmt_per” which measures the percentage of full bill payments in the last 6 months. 

I built 6 machine learning models and measured their performances by predict accuracy. The final model is simple decision tree model which has the highest predict accuracy of 82.26%. 

## Logic Regression Models
1.	Full Model: 0.8226
2.	Stepwise Logistic Regression: 0.8143
3.	Bayesian Model: 0.8155

## Decision Tree Models
1.	One Tree Model: 0.8263
2.	Bagging Model: 0.8135
3.	Random Forest: 0.8183

## CONCLUSION AND RECOMMENDATIONS
Credit card payment default can stem from various of factors.  Married men are high default risk groups.  The more the credit limit, the less the default risk. The final model I adopted, which is simple decision tree model, provide an interesting interpretation of key factors driving default. It suggests that if people paid bill in September, there are 89% chance they won’t default next month.  

The negative correlation of credit limit and default shows that the current credit scoring system is effective to certain extent but definitely not enough considering the default crisis. I suggest banks to investigate cardholders’ age, sex, marriage status, credit limit, payment history and reevaluate their weigh in credit approval and scoring system. They might need to build an effective credit card suspension system to cancel the accounts of certain cardholders obviously does not have the ability to pay off debt or keeps not paying on purpose. 

