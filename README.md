# 2020-Presidential-Election-Sentiment-Predictor
Utilized twitter API and fastText NLP library to scrape live tweets to predict the winner of the 2020 US Presidential Elections 
Project date: 2020-Oct-15 to 2020-Nov-03

# Project Design
## Tweet cleaning 
Since Twitter is an online forum, the majority of the text is informal and unconventional in nature. This includes a lack of capitalization and punctuation, relaxed grammar rules, and a frequent usage of emojis. Thus, both the training and analysis data needed to be pre-filtered. By converting all text to lower case, removing punctuation, and converting emojis to words, we effectively reduce the dictionary size of the NLP model. This is vastly important in preventing overfitting/unintended results in the data.
For example, consider these two sentences in the training example.
1. Positive sentiment: i love NLP!
2. Negative sentiment: I HATE NLP!
In this case, the language model may associate i and I with different sentiment weightings as they would represent different words. In reality though, the difference in sentiment arises from love/hate, and not I. 

To build upon this example for future improvements, lemmatization/stemming could be used to convert words such as 
good/better/best -> good
playing/played/play -> play

## Establishing a control and comparison
Extracting Twitter tweets using the Twitter API and Tweepy consists of specifying a hashtag and a certain number of tweets to scrape given a certain timeframe. This initially may seem fine, as we could simply scrape 5,000 tweets from both #Trump and #Biden and measure how many of them are positive. However, how do we know that the NLP model is classifying Tweets properly? 
One issue caused by this is due to our training vs testing set difference. Training data is pulled from all tweets, whereas our testing data consists of political tweets, which may potentially have differences in sentiment (eg more sarcasm, inside jokes, backhanded compliments, etc)

Thus, we decided to introduce some controls to get a better baseline understanding of the sentiment around twitter. Using hashtags that should be innately negative (#DumpTrump, #SlowJoe) and positive (#GoTrump, #GoJoe), analyzing sentiment from these hashtags should verify the validity of the NLP model for political tweets. 


## Result analysis
![image](https://user-images.githubusercontent.com/67357603/221340901-c27a9203-8509-424b-81f0-a5dc4b551415.png)

## Improvements
Although the project aimed to see results that agreed with the controls and comparisons, I believe there was too little data and too much noise to discern proper trends. Given more time to extract data with more tweets (~100,000), I believe proper trends could be extracted. API scraping speed was extremely slow, and exploring a better API would definitely improve upon the amount of data gathered (eg snscrape)  

# Training and data analysis
