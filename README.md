# Analyzing the Overwatch Subreddit for Hero Balancing

### Problem Statement

We would like to grab a ton of posts from subreddit, combine relevant text data, like the title and body, into a single column so that we can count vectorize the words more easily. Using pushshift's API, we need to collect the data without producing duplicates. Because of the limit on how many posts we can pull from subreddit, we need a timed loop in order to pull the amount of data we want. Once we've processed the data using using a count vectorizer, we'll use the data to fit a random forest regressor model and a naive bayes model for comparison.

### Executive Summary

Blizzard Entertainment, One of the world's most successful video companies, has asked us to help them with hero balance in their popular online video game, Overwatch.

Overwatch is a popular 6 vs 6 hero shooter where every hero has a unique set of flashy abilites. Some can fly, teleport, or deflect bullets. But because of this, Overwatch is inherently a difficult game to balance. As such, community feedback is important to the balance of the game and making it more fun. However, there are thousands of Overwatch players, each with different opinions about how the game should be balanced. We can't possbily listen to all of them. We need to prioritize what the community at large feels is the right direction for the game.

Community feedback on Overwatch is all over the internet. Websites like reddit are a gold mine of information that we can use to get a gauge of how players feel. We just need to extract that feedback, figure out which heroes are commonly discussed, identify problems that community has, and come to a conclusion about the next step blizzard should take in balancing their game.

As a seasoned veteran of Overwatch and an expert Data scientist, I can get the job done. I understand how the game is played and I'm somewhat connected to the overwatch community.

I've played Overwatch since the day it was released. I love playing the game and I want to keep it fun for as many people as possible and for as long as possible. So let's take game balance to the next level!

### Data Dictionary
The two dataframes that I pulled from subreddit are "ow" and "wow", which is the overwatch and world of warcraft subreddit data respectively. I then combine the two into a single dataframe cllaed "bliz", short for Blizzard. The dataframes have many features. There are only a few columsn that are actually important. They are listed below.

|Column|Type|Description|
|---|---|---|
|title|object|Title of the subreddit post.|
|selftext|object|The body of the subreddit post.|
|created_utc |int| The unix time the post was created. Measured in seconds and can be converted to a date and time.|
|datetime|datetime |The date and time the post was created. Created from the "created_utc" column. |
|text |object | A column I created containing a combined string from the "title" and "selftext" column.|

### Conclusion and Recommendation
The analysis of the data shows an increased amount of chatter about the hero Genji since June. This corresponds to around the same time that Genji recieved buffs in the experimental mode of overwatch. The overwatch subreddit community has become more vocal about this hero ever since the changes have gone through to the live version of the game. Calls to nerf the hero have noticeably jumped up from the pervious month of May. The concensus among the community seems to be that the buffs were too much. As such, i would recommend that blizzard look into nerfing Genji or reverting some of the buffs that he recieved earlier.  
