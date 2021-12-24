# Introduction

GameStop became the poster child of memestocks when the subreddit r/wallstreetbets started driving up the share price from a mere 2 dollars in April'20 to as high as 350 dollars in the last week of January'21.

![image](https://user-images.githubusercontent.com/68967551/147302976-a3db5fde-49b9-4388-818d-8ef58be83247.png)


The objective of this project was to: 
1. Analyze the how twitter reacted to this frenzy and get insights on the shift in the sentiment and topics discussed
2. Analyze if the shift in sentiment is impacting the immediate stock price movement or not

I used LDA for topic modeling and the VADER sentiment analyzer for sentiment analysis.

# Topic-modeling


a. Scraping tweets:
I extracted the tweets with hashtags **GME** and **GameStop**. As the goal was to analyze the shift in topics, I extracted the data for three separate time periods i.e. Oct'20-Dec'20 (Pre), Jan'21-Mar'21 and Apr'21-Sep'21 (Post). As Tweepy Python library can scrape the tweets of only the last 7 days, I used the snscrape package to scrape the older tweets for the stated timelines.

b. Data cleaning and exploratory data analysis:

