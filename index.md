---
layout: page
title: Home
subtitle: Beer Analysis
---



# Introduction



TODO 



# Analysis

In order to have a good idea of all this means we choosen to answer dig into our topic by trying 4 questions. Those questions....



## Research question 1

The first question that we could ask to ourselves is through the year the preferences of poeple has changed and evolved. Does some beers are more/less liked in 2003 than 2015 ?

To have an idea about this question, let's introduce 2 metrics that can show interresting result.



**Metric 1: Rating's average**

In this metric it is about grouping a set of beer together and take the mean of those beers. The changes of this metric []through time[] can be explained by two ways :

   * It shows that a group of beer is less/more appreciated through a certain period of time
   * It shows that the actual beers of this group get better through time
Those 2 explanation can also be seen as one. For instance if blonde beer become has a better rating average in 2015 than 2003, does this mean that blond beer has a better taste in 2015 or does it mean that poeple like more the blond beers in 2015 than in 2003. This is effectively quite subjective, but it tells the same at the end.



**Metric 2 : Number of rating**

This one is the more interresting : it measure the number of rating for a certain group of beer. This metric express a sort of popularity. 



To start we can see what is happening on each style of beer directly (clustering by style). When we take only beers and check for the style that have enough ratings, we can look for the style that have the most increase :



{% include fig_q1_3.html %}

*This figure represents the percentage of rating for each style per year.*



What we see here that the IPA beers have significantly gained a lot of popularity through the years.



On the other hand on the decrease side, there is only one the Pale Lager beer that is decreasing.



But as there are more than 90 types of beers in the dataset, this information  (as shown in the graph) is about only 2-3% of the total ratings and showing all the beers would not be a good idea.



In order to have something that we could interpret, one idea could be to group the style together. Having only few group would help to have more representative data. After some research and trial, it seemed that grouping the beers in 7 groups would made good grouping : the groups seem to follow the big families of beers and prevent beer styles to fall too easily in multiple groups.

The group choosen are : Acid beer, Amber beer, Blond beer, Dark beer, Pale Ale beer, White beer and other.

We can first evaluate the rating average on each of this groups through the year.



{% include fig_q1_1.html %}



The blonde beers seems to be more liked through time but let's compare this to the number of rating of this 6 groups :



{% include fig_q1_2.html %}

*This figure shows the percentage of rating for each group for each year*



This table combined with the previous one is interresting : as the rating of the blonde increase its total number of rating is decreasing. Also we can see the same result as above that Pale Ale beer become more and more popular.







# How to include a graph

This is how we include a plotly graph write the following line

{% include fig_q1_1.html %}



Then in the git of the website add the html file into the "\_includes" folder







