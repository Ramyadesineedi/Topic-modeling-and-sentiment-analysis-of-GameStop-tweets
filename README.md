# Introduction

GameStop became the poster child of memestocks when the subreddit r/wallstreetbets started driving up the share price from a mere 2 dollars in April'20 to as high as 350 dollars in the last week of January'21.

![image](https://user-images.githubusercontent.com/68967551/147302976-a3db5fde-49b9-4388-818d-8ef58be83247.png)


The objective of this project was to: 
1. Analyze the how twitter reacted to this frenzy and get insights on the shift in the sentiment and topics discussed
2. Analyze if the shift in sentiment is impacting the immediate stock price movement or not

I used LDA for topic modeling and the VADER (Valence Aware Dictionary and sEntiment Reasoner) sentiment analyzer for sentiment analysis.

# Topic modeling

a. Scraping tweets:
I extracted the tweets with hashtags **GME** and **GameStop**. As the goal was to analyze the shift in topics, I extracted the data for three separate time periods i.e. Oct'20-Dec'20 (Pre), Jan'21-Mar'21 and Apr'21-Sep'21 (Post). As Tweepy Python library can scrape the tweets of only the last 7 days, I used the snscraper package to scrape the older tweets for the stated timelines.

b. Data cleaning and exploratory data analysis:
Data cleaning involved:
- Removing punctuations, URLs, hyperlinks, emojis, stopwords and frequently appearing collection of words(ex: gamestop, gme, game, dont, like, ps5, xbox etc.)
- Making individual words from the sentences, lemmatization and creating a word corpus from all the sentences

Exploratory data analysis:
- Top 20 words by count for each period: This gives an idea on the top relevant words from tweets of each period
![image](https://user-images.githubusercontent.com/68967551/147367363-20275311-a75f-4bae-b953-40418261698d.png)

- Word cloud: Shows the top keywords of each period
![image](https://user-images.githubusercontent.com/68967551/147367537-d0c2f174-df1a-492c-8d47-cf80c29538b8.png)

c. Topic modeling results:
![image](https://user-images.githubusercontent.com/68967551/147378872-ce0a1dbd-9096-4c77-8134-06c3d16b8ac8.png)


The topic modeling output and the word cloud provides the below inference:
Before GameStop became a memestock, people were primarily discussing about the GameStop products, orders and retail competition in twitter.
Once the frenzy started in Jan'21 the major tweets included topics regarded shorting, reddit, stock trading, robinhood, SEC
Post April, there was a slight shift in the topics. While people were still tweeting about the GameStop stock, they also started tewwting abount the products in general. This indicates that the frenzy related to the GameStop as a memestock has slowly started dying down and we can expect that the stock price will start stabilizing.

# Sentiment Analysis using VADER

For this I took the stock prices and tweets for the month of September.  
Using the SentimentIntensityAnalyzer from VADER, we can get whether the tweet has a positive, negative or neutral sentiment and the score tells us how positive, negative or neutral the sentence is. We also get the compound score which is computed by summing the valence scores of each word in the lexicon, adjusted according to the rules, and then normalized to be between -1 (most extreme negative) and +1 (most extreme positive).
- If the compund score >= 0.05, then the sentiment is positive
- If the compund score <= -0.05, then the sentiment is negative
- If the compund score < 0.05 and > -0.05, then the sentiment is neutral

Once I got the sentiment scores and sentiments of the tweets, I took the count of all positive sentiment tweets by each day fo sepetember to get the total positive tweets by each day.

![image](https://user-images.githubusercontent.com/68967551/147390796-8765b659-b624-4cbd-8e3c-4f227ff7d7c5.png)

Then I compared this with each day's opening price with the number of positive tweets to see if the number of posiive tweets increased with respect to previous day and there was an increase in opening price with respect to previous day. 
Result: In 47% of the occasions, the tweet sentiment reflected the next day's stock movement.










