# Lobbyists4America
Tweet sentiment analysis on JSON file using Pyspark, Spark-NLP

## Hypothetical Client:
Helping Lobbyists4America understand relationships between congress members better through their tweets.
Using this intel to help them better target their clients’ lobbying efforts in Congress.

## Hypotheses:
- There will be clusters of like-minded politicians that can be drawn largely along party lines.
- There will be centres of influence (loud / influential voices) in these clusters that clients can target.
- Some themes will emerge as more topical in this time period

## Approach:
1. Exploratory analysis on over 1m tweets from members of Congress that has been collected:
  - Collect JSON file, and convert to Spark Dataframe
2. Use a Bag-of-Words approach to understand the main themes in this time period:
  - RDD data manipulation, flatmap and reduce to create annual corpora of frequently occurring words
  - NLTK stopword removal
  - Wordcloud to visualise results
3. Focus on the main themes, scoring active members’ tweets on their sentiment on these issues:
  - Spark-NLP to confirm main themes from previous step
  - TextBlob for sentiment scoring
4. Spark ML packages to find correlations between members, and identify clusters of like-minded members:
  - Spearman Rank Correlation between congress members on the pertinent issue of Healthcare
  - Spark's Bisecting K-Means clustering algorithm optimised using the silhoutte score to create 6 clusters of similarly minded members.


## Hypotheses Results:

### There will be clusters of like-minded politicians that can be drawn largely along party lines.
Proved: This was clear to see from those who referred to healthcare reforms as ACA vs those who called it Obamacare. Also clear to see from the clusters that emerged.

### There will be centres of influence (loud / influential voices) in these clusters that clients can target.
Proved: For example Cory Booker and Bernie Sanders were the members with the highest number of followers within their respective clusters.
For clients that want to influence this section of members, these influential Senators would be the highest value advocates of their messaging.
For clients who opposed ACA then members like Mike Lee could serve as a powerful voice.

### Some themes will emerge as more topical in this time periods
Proved: We found Healthcare was most important issue in this period.
