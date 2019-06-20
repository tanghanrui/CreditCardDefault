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
Accuracy:
1.	Full Model: 0.8226
2.	Stepwise Logistic Regression: 0.8143
3.	Bayesian Model: 0.8155

## Decision Tree Models
Accuracy:
1.	One Tree Model: 0.8263
2.	Bagging Model: 0.8135
3.	Random Forest: 0.8183

## CONCLUSION AND RECOMMENDATIONS
Credit card payment default can stem from various of factors.  Married men are high default risk groups.  The more the credit limit, the less the default risk. The final model I adopted, which is simple decision tree model, provides an interesting interpretation of key factors driving the default. It suggests that if people paid bill in September, there are 89% chance they won’t default next month. If they paid in both September and July, chances are 99% they will pay bills next month.

The negative correlation of credit limit and default shows that the current credit scoring system is effective to certain extent but definitely not enough considering the default crisis. I suggest banks to investigate cardholders’ age, sex, marriage status, credit limit, payment history and reevaluate their weights in current credit approval and scoring system. They might need to build an effective credit card suspension system to cancel the accounts of certain cardholders obviously does not have the ability to pay off debt or keeps not paying on purpose. 

## APPENDIX
Figure 1.   Distribution of outcome variable and some features

![image](https://user-images.githubusercontent.com/18519663/59875229-15472c80-9355-11e9-82a7-e011d122ebb3.png)

Figure 2.  The distribution of card holder’s age

![image](https://user-images.githubusercontent.com/18519663/59875235-1a0be080-9355-11e9-8a61-74a6b55cfad7.png)

Figure 3. Correlations between default_next_month, limit_bal, pay_amt_sept, and bill_sept

![image](https://user-images.githubusercontent.com/18519663/59875244-1d9f6780-9355-11e9-88bb-bd90d3dcf589.png)

Figure 4. Correlations between default_next_month,, education, sex, age, and marriage

![image](https://user-images.githubusercontent.com/18519663/59875254-22641b80-9355-11e9-9396-67a26bc5b998.png)

Figure 5. The relationship between default and credit limit

![image](https://user-images.githubusercontent.com/18519663/59875352-67884d80-9355-11e9-8fcb-4e76f2122bc0.png)

Figure 6. The relationship between default and sex

![image](https://user-images.githubusercontent.com/18519663/59875358-6d7e2e80-9355-11e9-8d69-7ff6ef60fc6b.png)

Figure 7. The relationship between default and marriage

![image](https://user-images.githubusercontent.com/18519663/59875363-7111b580-9355-11e9-9c23-f40150ce1b42.png)

Figure 8.  The relationship between default and bill amount in September

![image](https://user-images.githubusercontent.com/18519663/59875367-753dd300-9355-11e9-9a71-062ec5decb29.png)

Figure 9. Count of default_next_month for cardholder paid in full

![image](https://user-images.githubusercontent.com/18519663/59875372-7969f080-9355-11e9-8e84-12b567c1d613.png)

## FINAL MODEL: ONE TREE MODEL
![image](https://user-images.githubusercontent.com/18519663/59875274-2f810a80-9355-11e9-8592-fc292c9121fe.png)

![image](https://user-images.githubusercontent.com/18519663/59875281-34de5500-9355-11e9-82f3-d16459392a1f.png)

## BAGGING MODEL
![image](https://user-images.githubusercontent.com/18519663/59875291-39a30900-9355-11e9-9a02-8cd59f39eca9.png)

## RANDOM FOREST 
![image](https://user-images.githubusercontent.com/18519663/59875410-930b3800-9355-11e9-9071-1b3273d97176.png)

## LOGISTIC REGRESSION MODEL METRICS COMPARISON
![image](https://user-images.githubusercontent.com/18519663/59875422-97cfec00-9355-11e9-99a1-c2a626546772.png)

## DECISION TREE MODEL METRICS COMPARISON
![image](https://user-images.githubusercontent.com/18519663/59875430-9c94a000-9355-11e9-92ac-06c5ff323250.png)

