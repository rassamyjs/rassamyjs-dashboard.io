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


## Why Beer?

It isn't healthy to sit on a chair and all day and night. Once you start dreaming about your code, it's over. Your life is now consumed 
in the life of code. Being consumed in code can be a positive or negative depending on if you have fun or are struggling. You should get
a change of pace and get your mind off of code.

In this case, why not have a beer? Drinking can be a nice stress reliever for a long day of coding. A disclaimer however, you should drink
smartly, and drink safe.

We're at the point of wanting to try a beer right? Now you have to find out what kind you want to drink. That's where this dataset comes in.
It will show the top ten most reviewed beers and visualize the reviews of based off of the rubric. 

## The Codes 

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
| Pliny The Elder | 2527 |

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
| Pliny The Elder | 2527 | 4.59 | 4.39 | 4.45 | 4.63 | 4.59 |

## The Graph
A visual of the data to show the mean of the overall review score

![Bar Graph](/assets/img/beer_review_overall_review.png)

With the table, it might of been obvious. With an average of 4.59 out of 5, Pliny The Elder is the highest rated review of the ten most reviewed. Here is the link to get more info on [Pliny The Elder](https://https://russianriverbrewing.com/pliny-the-elder/).

## Some More Exploration
After checking out that Pliny The Elder was the best rated out of the ten, I wanted to look into the dataset some more. Looking at the data, I saw something interesting.

~~~
pliny.head()
~~~
One of the rows had someone rate a couple things with 3s and 4s but gave an overall review of 5

| Beer Name | Review Count | Aroma | Appearance | Palete | Taste | Overall |
| :------ |:--- |:--- |:--- |:--- |:--- |:--- |
| Pliny The Elder | 2527 | 4.50 | 4.00 | 3.00 | 3.50 | 5.00 |

I'm not the best at math, but I can see the math does not add up. There is some **FAKE NEWS/FAKE INFO** being spread over here. Okay, it might not be that serious. Perhaps someone who reviewed it didn't pay enough attention. To get a true average overall mean I need to add up the columns and do some division. 

~~~
pliny['Overall'] = ((pliny['review_aroma'] + pliny['review_appearance'] + pliny['review_palate'] + pliny['review_taste']) / 4)
~~~

This gives me a new column to compare the new overall mean review with the old one.
| Beer Name | User Review | Mean Review |
| :------ |:--- |:--- |
| Pliny The Elder | 4.59 | 4.52 |
~~~
compare = {'Mean Rating' : pliny['Overall'],
           'Reviewer Rating' : pliny['review_overall']}
~~~

![plot](/assets/img/beer_review_overall_comparison.png)

We can see that the user review was going off of .5 while the new mean goes off of .1. This makes the data more spread out. Does this change anything?

## Comparing Graphs

| Beer Name | User Review | Mean Review |
| :------ |:--- |:--- |
| 90 Minute IPA | 4.15 | 4.23 |
| India Pale Ale | 3.84 | 3.80 |
| Old Rasputin Russian Imperial Stout | 4.17 | 4.29 |
| Sierra Nevada Celebration Ale | 4.17 | 4.15 |
| Two Hearted Ale | 4.33 | 4.22 |
| Stone Ruination IPA | 4.07 | 4.18 |
| Arrogant Bastard Ale | 4.16 | 4.27 |
| Sierra Nevada Pale Ale | 4.24 | 4.00 |
| Stone IPA (India Pale Ale) | 4.26 | 4.21 |
| Pliny The Elder | 4.59 | 4.52 |

The original graph
![Bar Graph](/assets/img/beer_review_overall_review.png)

The new graph
![Bar Graph](/assets/img/beer_review_overall_other_mean_base.png)

Base off the table and graphs. We can see that the new means did not change much.
