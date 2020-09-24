---
layout: post
title: Beer Review
subtitle: Finding the top rated beer among the most reviewed
tags: [books, test]
---

---
This blog post will explore the dataset of the reviews of many kinds of beers found on [kaggle](https://www.kaggle.com/rdoume/beerreviews). 
This set of reviews is based off a simple rubric: the aroma, appearnace, palete, taste, and the reviewer's overall review. 

I am going to check out what was the most popular beers that were reviewed and see which one was the highest rated.


## Why beer?

It is not healthy to sit on a chair and all day and night. Once you start dreaming about your code, it's over. Your life is now consumed 
in the life of code. Being consumed in code can be a positive or negative depending on if you have fun or are struggling. You should get
a change of pace and get your mind off of code.

In this case, why not have a beer? Drinking can be a nice stress reliever for a long day of coding. A disclaimer however, you should drink
smartly, and drink safe.

We're at the point of wanting to try a beer right? Now you have to find out what kind you want to drink. That's where this dataset comes in.
It will show the top ten most reviewed beers and visualize the reviews of based off of the rubric. 

## The code to get to the graphs

~~~
data_copy['beer_name'].value_counts().head(10)
~~~
Using value counts to look at the list in the dataframe, I can look up how many times a beer was reviewed.

| Beer Name | Review Count | 
| :------ |:--- |
| 90 Minute IPA | 3290 | 
| India Pale Ale | 3130 | 
| Old Rasputin Russian Imperial Stout | 3111 |
| Sierra Nevada Celebration Ale | 3000 |
| Two Hearted Ale | 2728 |
| Stone Ruination IPA | 2704 |
| Arrogant Bastard Ale | 2704 |
| Sierra Nevada Pale Ale | 2587 |
| Stone IPA (India Pale Ale) | 2575 |
| Pliney The Elder | 2527 |
