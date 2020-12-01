---
layout: post
title: Stock Price Prediction using Tweets Sentiment
subtitle: An interactive visualization tool for exploring stock trends using Tweets sentiment 
cover-img: /assets/img/2020-12-01-pred.png
tags: [shiny, R, python, classifier, sentiment]
---

[_**Stock Price Prediction**_](https://cyjenn33.shinyapps.io/Tweets_Predict_Stock/) is a GUI built for the final project in CSE 6242 (Data and Visual Analytics) offered by Georgia Tech in 2020 Fall. This project aimed to provide an intuitive interface for users to examine the relationship between twitter sentiments and selected stock price.  

***Approaches***
This project included four approaches: a NLP package called _sentimentr_ was used to perform the sentiment analysis for tweets. GBM, SVM and other Python packages were used to do machine learning. A visual tool using _Shiny_ was created for presenting final results. Finally we evaluated our analysis results by checking correlations, ML metrics and running multiple simulations. 

***Data Collection***
Daily stock data for 30 major stocks was scripted from Yahoo Finance using Python. Available tweets data (~ 540 GB) was pulled directly from Twitter developer platform and internet archive. 

***Sentiment Score***
After cleaning raw data, we used _sentimentr_ to calculate sentiment score for each tweet. Then we added score of each day and weighted the score based on publisher's influence on twitter. 

***Predictive Modeling***
Our goal for modeling is to use sentiment scores and stock price data to predict whether an investor should buy or sell for a specific ticker on a specific date. Variables we used in our models included: 
- open price 
- sentiment score from tweets posted 
- stock volume and price change % on previous day

We run multiple binary classification models including Random forest, Gradient boosting and eventually we picked results from SVM model due to its best precision and highest accuracy.

***Evaluation***
Results had been evaluated by checking correlation between sentiment score and stock price movement. We also tried both including/excluding sentiment score variable in the model and simulated trade based on model predicted strategy and blind trading. It showed that sentiment score did positively impact on stock price and the model with sentiment score had higher out-of-sample accuracy. From simulation results, our predicted strategy was able to generate higher rate of return comparing to blind trading. 

***Visualization***
Finally a Shiny dashboard was built using R to better visualize results. It has a tab for EDA for tweets sentiment and stock price trends. On prediction tab, users can pick a date and ticker, it then will show whether users should buy/sell that ticker, and the corresponding buy-in probability. This tool also shows the price trend for that ticker in the following 2 weeks, and a frequency-based word cloud and a feelings chart for ticker-related tweets.
