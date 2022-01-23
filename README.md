# Real-time-Twitter-Sentiment-Analysis

## Intoduction
This project focuses on sentiment analysis on tweets using Apache Spark Streaming in Python. A Developer Academic Twitter account was created in order to have access to tweets. An end-to-end model was developed to stream data from Twitter, pre-process it (text cleaning/tokenization etc) and finally to find out the polarity and subjectivity of each tweet. The tweets streamed from Twitter were specific for a location around New York city in the US, including Massachusetts, Pennsylvania, New Jersey and Delaware. Also, the english language was specified and the tweets were about "vaccination" (the keyword). Tweepy, pyspark and textblob were the main python libraries used.

Two separate notebooks were created to successfully perform the sentiment analysis on tweets for specific location, language and keyword. The first notebook should be run first (letting the last cell running) and then the second notebook.

## Notebook_1: tweeypy_notebook
The first notebook named as tweepy_notebook.ipynb was created to connect to Twitter API and retrieve tweets using the Academic account credentials. In this notebook the Twitter account's credentials were authenticated and TweetListen was used to listen the tweets and then send the data through the TCP socket between Tweeter's API and Spark. A JSOM module had to be used to handle the data of JSON objects

### tweepy
Tweepy library in Python is required to connect to the Twitter API and build a pipeline for data streaming. The stream was built by using the imported classes of tweepy, *Stream* and *Stream Listener* and *OAuthHandler* was used to authenticate to Twitter.

### TweetListener
TweetsListener is a base class to listen tweets only and stop listening when a specific number of tweets collected or time listening is out. If both parameters are 0 then it can run forever.

### Socket
A socket is one endpoint of a two-way communication link between two programs running on the network. A socket is bound to a port number so that the TCP layer can identify the application that data is destined to be sent to.

## Notebook_2: SentimentAnalysis_Spark_notebook
The second notebook named as SentimentAnalysis_Spark_notebook.ipynb was created to receive the data from the TCP socket and pre-process it using pyspark. Then, sentiment analysis was applied using textblob and finally the each tweet and its sentiment analysis scores was saved in a parquet file (a data storage format). In order to achieve that though, Spark, Java and Hadoop environments had to be set up on Windows.

### PySpark
PySpark is an interface for Apache Spark in Python. It not only allows you to write Spark applications using Python APIs, but also provides the PySpark shell for interactively analyzing your data in a distributed environment. PySpark supports most of Spark’s features such as Spark SQL, DataFrame, Streaming, MLlib (Machine Learning) and Spark Core.

### TextBlob
TextBlob is a Python library for processing textual data. It provides a simple API for diving into common natural language processing (NLP) tasks such as part-of-speech tagging, noun phrase extraction, sentiment analysis, classification, translation, and more.

## Discussion
As shown from the sentiment analysis, most of the tweets in area of and around NYC are neutral about the vaccination (43.57%), whereas 32.63% are positive and 23.80% are negative. In a word-cloud of negative tweets, words like "unethical", "concerning", "employer", "demented", "mandate", "impose", "worse", "covid" are found that clearly show how negative people are about covid vaccination. However, the subjevtivity of positive tweets (0.225) was found to be higher than that of negative (0.215) and neutral (0.217) tweets. Also, most frequent word and phrases were retrieved, showing that most tweets, relative to vaccination, include Biden in their texts. That shows that people is combining vaccination with politics. According to literature some people's opinion is based on their political views, and vaccination rates wree significantly lower in countries with high percentage of Republican voters.

## Conclusion
The real-time dominant sentiments of the public opinion regarding covid vaccination showed that most people are neutral. However, a high percentage of the people are negative about how the government made vaccination mandatory. The subjectivity of the people was shown to be low (0.22 average). However, the most frequent was found to be Biden, showing how politics are involved in the vaccination/covid topic.

# References
- https://towardsdatascience.com/sentiment-analysis-on-streaming-twitter-data-using-spark-structured-streaming-python-fc873684bfe3
- https://towardsdatascience.com/step-by-step-twitter-sentiment-analysis-in-python-d6f650ade58d
- https://developer.twitter.com/en/docs/twitter-api/v1/tweets/filter-realtime/guides/basic-stream-parameters
- https://docs.oracle.com/javase/tutorial/networking/sockets/definition.html#:~:text=A%20socket%20is%20one%20endpoint,address%20and%20a%20port%20number.
- https://spark.apache.org/docs/latest/api/python/index.html#:~:text=PySpark%20is%20an%20interface%20for,data%20in%20a%20distributed%20environment.
- https://bmcpublichealth.biomedcentral.com/articles/10.1186/s12889-021-12432-x
