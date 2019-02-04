
# Project 3: Web APIs & Classification - Executive Summary

## Goals:  
1. Using Reddit or Pushshift.io API, collect posts from two subreddits of my choosing (r/cats and r/dogs).
2. Use NLP to train a classifier model on which subreddit a given post came from.
3. Stretch goal: Use sentiment analysis to solve the age-old debate of cats vs dogs.

## Process:  
- Data collection: Reddit and pushshift.io APIs
- Data cleaning and EDA
- Preprocessing and Modeling
- Evaluation
- Conclusions

## Data Collection:  
Both Reddit API and pushshift.io APIs were tested as methods for collecting data on subreddit posts. Pushshift was used for the final data collection. The main disadvantage of the Reddit API is the limit of  only the most recent 1,000 posts at any time. Data collected from pushshift was 20,000 comments (10,000 each from /r/cats and /r/dogs subreddits)
I analyzed comments for this project, as cat submissions are mostly photos and dog submissions are mostly text (/r/dogs doesn’t allow photo posts, only links to photos). The comments are more comparable between the two subreddits.

## Data Cleaning and EDA
The following were removed from the comments: html, hyperlinks, punctuation, words with 2 or fewer letters, whitespace including line returns, non-standard characters (emoji). Duplicate messages were dropped. There were approximately 1200 duplicate moderator bot messages (600 in cats and 600 in dogs). After cleaning, there were approximately 18,000 records total, still split approximately in half by cat and dog classes. Words in the comments were lemmatized and stop words were removed. Preliminary EDA showed that of the 30 most frequent words in each class, approximately 1/3 were unique to the class and 2/3 were the same in both.

## Preprocessing and Modeling / Evaluation
CountVectorizer and TfidfVectorizer from scikit-learn were used to convert the text data to numeric features. CountVectorizer achieved a better accuracy score for a baseline logistic regression model. Logistic regression, Random forest, and Multinomial naive Bayes models were tested with Gridsearch. Logistic regression performed the best.

## Bonus: Sentiment Analysis
Sentiment analysis using TextBlob showed that comments in /r/cats had a higher mean positive sentiment and had more comments in the highest positive sentiment range (0.5 - 1). This matches my subjective analysis of the most common unique words, as /r/cats included words like 'beautiful', 'best', 'cute' and 'lol', while /r/dogs included 'training' and 'work'. 

## Conclusions
Using CountVectorizer and Logistic regression model achieved the best accuracy scores (train / test scores: 0.8481 / 0.8543).

Potential improvements for future: collect more training data, do more data cleaning and preprocessing (remove more stop words i.e. numbers, stem/lemmatize i.e. -ing verbs), more intensive gridsearching to optimize models, include n-gram parameter in gridsearch, try more models (boosting, SVM)

Sentiment analysis showed that the comments in /r/cats were more positive overall than comments in /r/dogs, however we cannot conclude whether cats or dogs are superior. More research (and cute animal photos) are needed.

