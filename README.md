# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Targeted Podcast-Based Marketing on Reddit
#### by Benjamin Haile


## Problem Statement

Hardwire is a marketing firm specializing in gaming and online media. We want to tailor digital marketing to social media users based on the interests they express online. One avenue we’re pursuing is the design of an algorithm for understanding a user’s interests based on Reddit posts. We’re testing our algorithm on the audiences of two podcasts we’ve worked with before: the Rooster Teeth Podcast and Castle Super Beast. Both of these podcasts focus on video games, while also touching on different media. We expect some overlap in audiences between the two, but overall, these audiences have subcultures with different interests. To complete the algorithm, we need a classification model that will predict which podcast’s subreddit a user posts in based on the post’s title. The algorithm can then show a user relevant ads based on key words associated with that podcast.

I will first fit a logistic regression, and then fit different types of naive Bayes models if the original model requires more complexity. Models will be evaluated on accuracy, and variance and AUC will also be considered.


## Executive Summary

I used the Pushshift API to collect data on posts in the subreddit r/RoosterTeeth and r/TwoBestFriendsPlay (the former name of Castle Super Beast). I adjusted my function to draw a roughly equal amount of data of each subreddit. Preliminary data cleaning involved checking for null values and quantifying the names of the subreddits, for use in a classification model. I selected Rooster Teeth(RT) as 0 and Castle Super Beast(CSB) as 1. I chose the title of the post as my independent variable. This seemed to be the simplest choice, requiring less text to process. I filtered the data for unique values of 'title', to avoid overcounting any words. 

To explore the data, I created bar charts of the most common words in each subreddit, and between the two of them. This demonstrates the difference in audience interests. Understanding the unique interests of the podcasts' listeners is relevant given our ultimate goal of targeted marketing. I then fit a logistic regression model using 'title' to predict 'subreddit'. I also fit two naive Bayes models, a multinomial and a Gaussian, trying to reduce variance. The multinomial model proved to be the most accurate. This model is fit to complete our algorithm. Moving forward, we should also keep the differences in audience interest in mind when designing targeted marketing.

---

### Datasets

The data has been pulled from the relevant subreddits using the Pushshift API.

[Rooster Teeth subreddit](https://www.reddit.com/r/roosterteeth/)

[Castle Super Beast subreddit](https://www.reddit.com/r/TwoBestFriendsPlay/)

### Data Dictionary

|Feature|Type|Description|
|---|---|---|---|
|title|object|The title of the subreddit post|
|subreddit|int|0: Rooster Teeth, 1: Castle Super Beast|


## Conclusion and Recommendations

Our model makes accurate predictions, and is ready to be added to our larger algorithm. Using this algorithm will predict which podcast a user prefers based on their Reddit posts and tailor the ads they see accordingly. CSB listeners are much more likely to post about video games specifically, so their ads should be for other games. They seem especially interested in games from Capcom(developers of Devil May Cry) and Nintendo(developers of SSBU). Rooster Teeth fans, conversely, post mostly about RT media, rather than specific games. Their ads should be for content made by similar production companies. Moving forward, we can apply this algorithm to the subreddits of other podcasts to reach more audiences. We can also start developing targeted marketing based on how audiences use YouTube and Twitch.
