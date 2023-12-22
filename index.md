---
layout: page
title: Home
subtitle: Beer Analysis
---

#  Introduction



Beer is one of the most used alcoholic beverages in the world. Its consumptions has exceeded more that 185 million kiloliters in recent years. As a beverage which hundreds of millions of people drink, its taste and styles has experienced considerable evolution. As any business understanding consumer preferences of beer styles is crucial for producers, distributors, and enthusiasts alike. This website digs into a comprehensive beer dataset, aiming to show the history of beer preferences over time. We are going to investigate what variables are contributing in beer preferences and how does they evolve through time. We will also see whether beer preferences vary depending on the country of the users that are drinking them, or do different countries have different beer preferences



# Analysis

In order to have a good idea of all this means we choosen to answer dig into our topic by trying 4 questions. 

RQ1: How does beer preferences evolve? How does different beer styles become more popular by the time? Do they experience a decay in their popularity as time goes?



RQ2: Which aspects of beers are associated with the popularity of beer the most? Does the importance of these aspects change during the time?



RQ3: What is the estimated lag time between introducing a new beer and the gain of popularity on average?



RQ4: Are there any difference geographically between the trends of beer?



## Research question 1

The first question that we could ask to ourselves is if through the years the preferences of poeple has changed and evolved. Does some beers are more/less liked in 2003 than 2015 ?

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





## Research question 2

In this research question we would like to answer, which aspect of the beer in the ratings (aroma, appearance, taste, pallate and overall rate) have the highest impact on the popularity of the beer. First lets visualize the ratings for each of these aspects during the time we have data, to see if the perception of reviewers towards different beer styles in each of these aspects is changed or not. 





![4_metrics_style](https://github.com/ambor1011/NeverEnoughData/raw/master/assets/img/4metric_style.jpg)



To answer this question we should define the popularity in this context. For the research question we define the popularity as follow.



**Metric 3**

Populairty = scaled number of reviews per beer style per year * average rating per beer style per year.



The reason to construct the populaity like this is the fact that, the number of reviews are not constant during different years therefore we need to devide the number of reviews for each beer style per year by total number of reviews in that year to find a relative attaction of certain beer style for writting the review. But having number of review is not only pillar to quality and acceptance of a beer, maybe we can have a bad beer with high number of reviews. Therefore, we multipy the relative number of comments to average rating for that year and beer style. This metric could represent the populaity of beer. 



Now we have our dependant varibale, lets talk about the independant varibales. We are going to  use aroma, appearance, taste, pallate and overall rate as our IVs. But before construcitng the regression we need to make sure our independant variables are indeed independant. Therefore, we need to check if they have corrolation with eachother or not. Unfortunately, these metrics are corrolated with each otehr therefore, we can not construct our regression and therefore we can not conclude that any of these metric is more significant because they are related.



## Research question 3

The third research question tries to assess the time it takes for a beer to get popular. This analysis holds on two date definitions : the date the beer is released ; and the date it becomes popular.

This analysis, to be relevant must only be ran on beers with a high number of ratings, so that the beer is really popular, we've chose 500.



The release date is defined as the earliest rating we have in our dataset, to avoid beers released before dates in our dataset, we neglect all beers appearing in ratings in the two first years of activity of the website (2000, 2001).



The "popularity reach date" is defined as the average between the time taken to reach 500 ratings and the time to reach the highest increase in number of ratings. This average smoothes the differences in popularity (500 ratings threshold) and trendyness.



 ![fig_q3_1](https://ambor1011.github.io/NeverEnoughData/raw/master/assets/img/fig_q3_1.jpg)

 One can see that the distribution is a righ skew, with a median at 4 years.

 

###  What could influnce this lag time ?



#### Popular breweries

Some breweries have more than on popular beer, those can be large corporations like AB-INBEV (largest brewery in the world) with a large marketing power or smaller craft breweries that happen to do great beers. We will say that the popualr breweries are the once appearing more then 10 times in the popular beers.



![fig_q3_2](https://ambor1011.github.io/NeverEnoughData/raw/master/assets/img/fig_q3_2.jpg)

 

 A linear regression tells us that coming from a popular brewery decreases by 1.27 years the time to reach popularity.

 

####  Breweries from the US

A large part of the users come from the US, as a lot of beers in the website are craft beers that might not be easely exported. 



![fig_q3_3](https://ambor1011.github.io/NeverEnoughData/raw/master/assets/img/fig_q3_4.jpg)



 A linear regression tells us that coming from an american brewery decreases by 1.41 years the time to reach popularity.

 

####  Popular styles

Some styles appear more than the others in the popular beers.

![fig_q3_4](https://ambor1011.github.io/NeverEnoughData/raw/master/assets/img/fig_q3_4.jpg)



In conclusion, popular beers take around 4 years to reach popularity, this can be highly influenced by the popularity and location of the brewery but also by the style of the beer crafted and the overall_score of the beer.



## Research question 4

In this section we try to analyze how beer preferences change in different parts of the world. We analyze both popularity (taken as the number of ratings) as well as appreciation (taken as the mean rating). We focus on beer styles, the ones provided in the data frame, and not on specific beers.



###  Some initial information about the data

Our users come from 222 different locations (50 of which are US states) from 6 continents. Looking at the average ratings for each country, we can already see that there are significant differences between regions. Figure x below shows the distribution of the average ratings for all the regions. 



{% include fig_q4_1.html %}



The standard deviation is of 0.16 and we can see regions with averages below 2.8 and some above 3.4. This is interesting because it already shows that there are some differences between regions in how they grade their beers. This is significant, therefore we should prioritzie relative comparisons rather than focusing on absolute values. 



### Most popular beer styles over the world

The most popular beer styles in the world are the India Pale Ale (IPA), the Imperial Stout, the Pale Lager, the American Pale Ale and the Imperial IPA. A more specific description can be found by separating the data depending on the countries (the US states have been merged into one country). 

We first regroup the countries by continents. Some differences can already be spotted.  For example in Asia, Europe and in North America the most rated beer style is the IPA while in Africa, Oceania and South America it is the Pale Lager.  This is already quite interesting. Considering the number of ratings equivalent with popularity it would seem that the most popular beers for these continents are different, implying some difference in tastes (or availability). However going into more detail, looking for the most rated beer styles in various parts of Europe we always fall on the IPA. 

More detail can be found when looking directly at countries. We plot below a histogram of the most rated beer styles for various countries.



{% include fig_q4_2.html %}



As can be seen, in the majority of the countries in the world, the IPA as well as the Pale Lager are the most rated beer styles. It is interesting to note that for some countries the most rated beer style come from specific countries (Belgian Ale, German Hefeweizen, Czech Pilsner (Světlý)). We can verify that these countries do indeed correspond to the countries in from which these beers originate. The Belgian Ale for example is the most popular beer style in Belgium and the Netherlands while the Czech Pilsner (Světlý) is the most popular beer in the Czech republic. We will later see that this isn't reflected in the ratings of these beers.



### Most liked (best rated) beer styles in the world

Now that we have found the most rated beer styles let's see if these correspond to the best rated beer styles as well or if they are different. The 5 most liked beer styles in the world are Imperial Stout, the Abt/Quadrupel, the Lambic Style - Gueuze, the Imperial Porter and the Imperial IPA.  We can already see from this that these do not match the most rated styles. A more precise analysis can be done looking more into detail into the best rated styles by continent. Choosing beers with more than 50 ratings per continent we find that the most liked beer styles are the ABT/Quadrupel for Africa, North America, Oceania, and south America while the Imperial Stout is the preferred style for Asia and Europe. Beer styles such as the Lambic Style - Gueze also appear quite often but rathe in second or third positions.

Going more into detail, looking at countries rather than continents, the situation is a bit different. We plot below a histogram of the best beer styles. 



{% include fig_q4_3.html %}



As can be seen it is the Pale Lager which is the beer style that is the best rated in most countries with the German Hefeweizen coming in second. This shows that grouping by region smooths out the differences between the countries.



Finally it is interesting to note that the Belgian Ale is only the 50th most enjoyed beer style in Belgium while the  Czech Pilsner (Světlý) is 60th in the Czech republic while at the same time being the most enjoyed beer style in Japan. 





## Ethical Risk

We don't know the reviewer's identity or their distribution on age, gender, and sensitive attributes. This fact is good because the risk of being traced back to reviewers could ensure their privacy. However, when we don't have any insights into these attributes, we may generalize our findings to the whole society. Imagine a scenario where most of the reviewers are men and mid-aged; then, all the deductions for all research questions are heavily biased. Therefore, any use of such an analysis could be discriminative regarding gender, age, and ethnicity. 



# 


