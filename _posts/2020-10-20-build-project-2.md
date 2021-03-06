---
layout: post
title: Hotel Cancelations Pandemic Special 
subtitle: Building a model to predict booking cancelations
tags: [books, test]
---
---

## Into

I'll be building a model for booking cancelations for guest at a hotel. Comparing the models with date and random splits and comparing those model with a model that features Covid. 

## Leaky data

First I looked at some featuress that may give the result of staying in the hotel to prevent data leaks.
There was another feature that was exaclty the same as my target called `'reservation_status'`.  
The first iterations of testing I was using dates as a feature. Those dates gave my model score an accuracy of 99%. It ended up being a very important features to determine the score and was overfitting the model. 

## Models

The prediction I want to find is a yes or no question. If a guest has canceled a booking or not. This means the models I will use will be for classification.
To start out, I will build a logistic regression model and a random forest classifier tree model. I want to see if a date split or random split will give a better score and when you would use one over the other. My feature I will predict is `is_canceled`. For the time split, I will train on data before 2017 and test on 2017. For the random, it will be 80/20.

- My baseline accuracy was around 60%. 

- Using the logistic regression model, with the date split I got a test score of around 73%. With random split, the score was around 77%

- Using random forest, my scores were 76% for a date split and 86% for random split. 

| Model | Date Split | Random Split |
| :------ |:--- |:---|
| Logistic Regression | 73% | 77% |
| Random Forest | 76% | 86% |

Next I wanted to treat this data like it was 2020 going into 2021 with the pandemic going on. I created a new feature called 'pandemic' and applied it to 2016 and 2017. I featured engineered the target to have the month of April to July be all cancelations due to Covid-19 and ran the models again.

- the pandemic base line was 55%

- Using the logistic regression model, with the date split I got a test score of around 54%. With random split, the score was around 65%

- Using random forest, my scores were 61% for a date split and 81% for random split. 

| Pandemic Model | Date Split | Random Split |
| :------ |:--- |:---|
| Logistic Regression | 54% | 65% |
| Random Forest | 61% | 81% |


## Interpretation and Conclusion

Comparing the models, after adding the 'pandemic' feature, both models preformed worse than the previous ones. In both models, the random split showed higher scores compared to the date split model. After adding features, the logistic model is actually lower than the baseline. 

![Feature Importance](https://raw.githubusercontent.com/rassamyjs/rassamyjs-dashboard.io/master/assets/img/fi_rfm.png)
![Permutation Importance](https://raw.githubusercontent.com/rassamyjs/rassamyjs-dashboard.io/master/assets/img/pi_rfm.png)

Comparing the important features, feature importance has lead_time, adr, and deposit_type at the top. Permutation importance has deposit_type, total_of_special_requests, and lead_time at the top. looking at what they all mean, lead_time is the time between starting and completing a process. Adr is alternative dispute resolution. Deposit_type consist of: no deposit, nonrefundable, refundable. Of the two, permutation holds more weight for me because I can agree with what it defines as important. 

![Feature Importance](https://raw.githubusercontent.com/rassamyjs/rassamyjs-dashboard.io/master/assets/img/fi_pandemic.png)
![Permutation Importance](https://raw.githubusercontent.com/rassamyjs/rassamyjs-dashboard.io/master/assets/img/pi_pandemic.png)

Looking at these graphs, it appears that adding a pandemic feature appears in the top ten importances, but it falls on the bottom half. The feature importances are similiar and having an agent replaces the special request on permutation importances.

![Confusion Matrix](https://raw.githubusercontent.com/rassamyjs/rassamyjs-dashboard.io/master/assets/img/confusion_matrix.png)

Looking at the confusion matrix, for this dataset, having a false positive report would be worse than a false negative. 

To wrap it up, the appearance of a pandemic brings down both my models. However, the model doesn't give a pandemic too much importance.
