# Real-time-Twitter-Sentiment-Analysis

## Intoduction
This project focuses on sentiment analysis on tweets using Apache Spark Streaming in Python. A Developer Academic Twitter account was created in order to have access to tweets. An end-to-end model was developed to stream data from Twitter, pre-process it (text cleaning/tokenization etc) and finally to find out the polarity and subjectivity of each tweet. The tweets streamed from Twitter were specific for a location around New York city in the US, including Massachusetts, Pennsylvania, New Jersey and Delaware. Also, the english language was specified and the tweets were about "vaccination" (the keyword). Tweepy, pyspark and textblob were the main python libraries used.

Two separate notebooks were created to successfully perform the sentiment analysis on tweets for specific location, language and keyword. The first notebook should be run first (letting the last cell running) and then the second notebook.

## Notebook_1: tweeypy_notebook
The first notebook named as tweepy_notebook.ipynb was created to connect to Twitter API and retrieve tweets using the Academic account credentials. In this notebook the Twitter account's credentials were authenticated and TweetListen was used to listen the tweets and then send the data through the TCP socket between Tweeter's API and Spark.

### TweetListener
TweetsListener is a base class to listen tweets only and stop listening when a specific number of tweets collected or time listening is out. If both parameters are 0 then it can run forever.

### Socket
A socket is one endpoint of a two-way communication link between two programs running on the network. A socket is bound to a port number so that the TCP layer can identify the application that data is destined to be sent to.

## Notebook_2: SentimentAnalysis_Spark_notebook
The second notebook named as SentimentAnalysis_Spark_notebook.ipynb was created to receive the data from the TCP socket and pre-process it using pyspark. Then, sentiment analysis was applied using textblob and finally the each tweet and its sentiment analysis scores was saved in a parquet file (a data storage format). 

### PySpark
PySpark is an interface for Apache Spark in Python. It not only allows you to write Spark applications using Python APIs, but also provides the PySpark shell for interactively analyzing your data in a distributed environment. PySpark supports most of Spark’s features such as Spark SQL, DataFrame, Streaming, MLlib (Machine Learning) and Spark Core.

### TextBlob
TextBlob is a Python library for processing textual data. It provides a simple API for diving into common natural language processing (NLP) tasks such as part-of-speech tagging, noun phrase extraction, sentiment analysis, classification, translation, and more.

## Conclusion


# References
https://towardsdatascience.com/sentiment-analysis-on-streaming-twitter-data-using-spark-structured-streaming-python-fc873684bfe3
https://developer.twitter.com/en/docs/twitter-api/v1/tweets/filter-realtime/guides/basic-stream-parameters
https://docs.oracle.com/javase/tutorial/networking/sockets/definition.html#:~:text=A%20socket%20is%20one%20endpoint,address%20and%20a%20port%20number.
https://spark.apache.org/docs/latest/api/python/index.html#:~:text=PySpark%20is%20an%20interface%20for,data%20in%20a%20distributed%20environment.
