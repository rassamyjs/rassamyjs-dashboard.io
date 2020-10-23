---
layout: post
title: Hotel Cancelations Pandemic Special 
subtitle: Building a model to predict booking cancelations
tags: [books, test]
---
---

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


## Interpretation 

In both models, the random split showed higher scores.

