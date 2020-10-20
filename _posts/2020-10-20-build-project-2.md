---
layout: post
title: Hotel Cancelations 
subtitle: Building a model to predict if someone will cancel a hotel reservation or not
tags: [books, test]
---
---

I am going to create several models and compare them to see which will give the best prediction outcome. To start out, I will build a logistic regression model and a tree model using the bare minmum of wrangling to make basic models to go off of. 

## Leaky data

First I looked at some columns that may give the result of staying in the hotel such as the reservation status and if arrival date also counts as a data leak.

## Models

To start out, I will build a logistic regression model and a tree model using the bare minmum of wrangling to make basic models to go off of. 

I split my model by date with the year 2016 as my training, 2016 as validation, and 2017 for a testing data. I started with an XGBoost tree model first and ended up with a validation accuracy of 75%. Then I decided I wanted to use more of my data for training. I then changed the split to 2015-2016 for training and 2017 for validation. I ended up with a higher validation score of 77%. Using logistic regression, I had a validation score of 73%. Using XGBoost gave me a higher score.

Looking at the feature importances from the XGBoost model, deposit type was the highest followed by previous cancellations amd parking space. Using permutation importance, deposit type was still high up, but room types ended up being higher as well. 
