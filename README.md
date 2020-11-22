## Overview 

Within the Jupyter Notebook included, multiple Natural Language Processing 
techniques are leveraged to perform the tasks outlined below.  The data being 
manipulated and analyzed comes from the NewsAPI and specifically focuses on 
articles pertaining to Bitcoin and Ethereum news.  

- Sentiment Analysis
- Word Tokenization
- N-Gram & Word Frequency Analysis
- Word Cloud Generation 
- Named Entity Recognition 

## Findings

Based on sentiment analysis of the dataset, Ethereum proved to be superior over Bitcoin.
Ethereum had a higher mean positive score (0.061 vs. 0.052),
a higher mean compound score (0.168 vs. 0.066), a higher max positive score
(0.297 vs. 0.229), and a lower max negative score (0.132 vs. 0.203) when 
compared to Bitcoin.  

When analyzing word frequency, quite a few of the same key words came up for
both coins.  PayPal was one of the most common words for both coins, as was 
char and cryptocurrency.  Reuters, London, and virtual came up often for both 
coins as well, which can be more easily identified via the word cloud that was 
generated.  In terms of Named Entity Recognition, ORG, PERSON, and GPE were some
of the most common entities to come up. As a big picture analysis of both coins, 
the sentiment is mostly neutral for both coins and both are making news
regularly, based on the article count that was available.  The market for both 
coins seems to be continually growing and both coins are discussed in similar 
places and context across the industry.  It would be worth performing continued
analysis on both coins to determine where prices may go and identify opportunities 
that may arise. 

### Data Preparation & Sentiment Analysis

To retrieve data for analysis the NewsAPI was leveraged.  All news articles in 
English that pertained to Bitcoin and Ethereum were pulled.  A total of 4,026 
articles were found pertaining to Bitcoin and 1,175 were found pertaining to 
Ethereum.  However, due to limitations from the free API service, only 20
articles for Bitcoin and 16 for Ethereum were able to be pulled and put into a 
dataframe for analysis.  Text limitations also apply with the free service API. 

A function was defined to extract all necessary content from the API, complete 
sentiment analysis (positive, negative, neutral, and compound scores), and
return a dataframe of the data.  Alternatively, a for-loop was also created 
to perform the same task.  The for-loop was utilized to pull Bitcoin data and put 
it into a dataframe and the function was utilized to pull Ethereum data and put it 
into a dataframe.

When analyzing the description data of both dataframes it is clear that Ethereum
yielded the highest mean positive score, with a score of 0.061.  This is in 
comparision to Bitcoin's mean positive score of 0.052.  This proves that on 
average across all articles analyzed Ethereum had more positive sentiments.  
As for the highest compound score, Ethereum outperformed Bitcoin
once again.  Ethereum saw a high compound score of 0.95 in comparison to Bitcoin's
high compound score of 0.82.  For comparison purposes it is interesting to note
that Ethereum had a low compound score of -0.42 vs. that of Bitcoin at -0.72. 
One final piece of descriptive data reviewed was the highest positive sentiment
score.  Once again Ethereum led Bitcoin, with max positive sentiment scores of 0.297
and 0.229 respectively.  It is worth noting that Bitcoin had an article sample 
size of 20 in comparison to 16 articles sampled for Ethereum.  This could skew 
data slightly. 

### Tokenization, N-Grams, & Frequency Analysis

To perform further analysis on the article data discussed, tokenization had to
occur.  A function was created to tokenize all text data from each article (word tokenized). 
A new column was created within each dataframe to store the
tokenized text.  Following tokenization, N-Grams were generated for each coin.
An N value of 2 was used (bigram) and a count of each bigram was performed. 
The most common 20 bigrams was listed for each coin.  Finally, a word count
was performed to find the most common words across all articles combined for each
coin.  The "token_count" function was leveraged to perform this task and the top
10 words for each coin were returned. 

### Word Clouds & Named Entity Recognition

In an effort to visualize word count and commonly used words across all articles
for each coin, word clouds were generated.  The size of the word in each cloud
represents a word more commonly used across all articles.  All words were 
included in each word cloud, but limitations can be placed to show only the
top number of words, if desired (max_words = X). 

The final analysis completed was Named Entity Recognition.  All articles had to
be combined for each coin prior to generating the NER model.  Once all articles
were combined into a "big string" the models were generated.  As can be viewed, 
the NER models outline the entities of each article and highlight them accordingly. 
Examples of common entities found across both coins are: ORG, PERSON, DATE, GPE, 
and CARDINAL.  As a final step, all entities were listed for each coin 
(word : entity format).  


