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
Using value counts to look at the list in the dataframe, I can look up how many times a beer was reviewed. In this case, I'm looking for the ten most reviewed beers.

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

As you can see there is quite a bit of reviews going on about beer. I guess I'm not the only one that enjoys a cold beer! We have 90 Minute IPA with the highest review count with 3290 reviews.

Now lets find out what the average review is for these picks. 
~~~
nin_min_ipa = ['90 Minute IPA']
condition2 = data_copy['beer_name'].isin(nin_min_ipa)
ninety_minute_ipa_subset = data_copy[condition2]

mean1 = mean(ninety_minute_ipa_subset['review_overall'])
~~~

These codes will be able to give me the means of what I want to see.

| Beer Name | Review Count | Aroma | Appearance | Palete | Taste | Overall |
| :------ |:--- |:--- |:--- |:--- |:--- |:--- |
| 90 Minute IPA | 3290 | 4.21 | 4.19 | 4.18 | 4.33 | 4.15 |
| India Pale Ale | 3130 | 3.76 | 3.86 | 3.76 | 3.80 | 3.84 |
| Old Rasputin Russian Imperial Stout | 3111 | 4.20 | 4.37 | 4.23 | 4.34 | 4.17 |
| Sierra Nevada Celebration Ale | 3000 | 4.08 | 4.23 | 4.08 | 4.19 | 4.17 |
| Two Hearted Ale | 2728 | 4.27 | 4.15 | 4.14 | 4.31 | 4.33 |
| Stone Ruination IPA | 2704 | 4.12 | 4.20 | 4.14 | 4.27 | 4.07 |
| Arrogant Bastard IPA | 2704 | 4.34 | 4.18 | 4.18 | 4.35 | 4.16 |
| Sierra Nevada Pale Ale | 2587 | 3.91 | 4.00 | 3.97 | 4.11 | 4.24 |
| Stone IPA (India Pale Ale) | 2575 | 4.24 | 4.14 | 4.14 | 4.30 | 4.26 |
| Pliney The Elder | 2527 | 4.59 | 4.39 | 4.45 | 4.63 | 4.59 |


