<h3 align="center"> WERATEDOGS – TWITTER ARCHIVE FOR DATA WRANGLING </h3>

<h4 align="center"> By Manon Mason </h4>


## Table of Contents
- [Installation](#installation)
- [Project Motivation](#motivation)
- [Project Steps Overview](#overview)
- [Project Goal](#goal)
- [Project Details](#detail)
- [Step 1: Gathering Data](#gathering)
- [Step 2: Assessing Data](#assessing)
- [Step 3: Cleaning Data](#cleaning)
- [Step 4: Storing Data](#storing)
- [Step 5: Analyzing and Visualizing Data](#analyzing)


## Installation<a name="installation"></a>

This project was completed on Jupyter Notebook IDE, using Python 3. The libraries used were:
-	Matplotlib
-	Seaborn
-	%matplotlib inline
-	Pandas as pd
-	Numpy as np
-	Requests
-	Tweepy
-	Os
-	Json
-	Image from PIL
-	Bytes IO from io

## Project Motivation<a name="motivation"></a>

This project is part of the Advanced Data Wrangling course, from the Data Analyst Udacity Nanodegree. 
Using Python and its libraries, I will gather data from a variety of sources and in a variety of formats, assess its quality and tidiness, then clean it. 
The dataset that I will be wrangling, analyzing and visualizing is the tweet archive of Twitter user @dog_rates, also known as WeRateDogs. WeRateDogs is a Twitter account that rates people’s dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10, the numerators though are almost always greater than 10. 
WeRatedogs downloaded their Twitter archive and sent it to Udacity via email exclusively for us to use in this project. This archive contains basic tweet data (tweet ID, timestamp, text etc) for all 5000+ of their tweets as they stood on August 1, 2017.

## Project Steps Overview<a name="overview"></a>

The steps in this project are as follows:
-	[Step 1: Gathering Data](#gathering)
-	[Step 2: Assessing Data](#assessing)
-	[Step 3: Cleaning Data](#cleaning)
-	[Step 4: Storing Data](#storing)
-	[Step 5: Analyzing and visualizing Data](#analyzing)


## Project Goal<a name="goal"></a>

Wrangle WeRateDogs Twitter data to create interesting and trustworthy analyses and visualizations. Additional gathering, then assessing and cleaning is required.

## Project Detail<a name="detail"></a>
In this project, I will work on the following three datasets.

<b>Enhanced Twitter Archive.</b>
The WeRateDogs Twitter Archive contains basic tweet data for all 5000+ of their tweets, but not everything. One column contains each tweet’s text, which has been used to extract rating, dog name, and dog ‘stage’ (I,.e. doggo, floofer, pupper and puppo). Out of the 5000+ tweets, only tweets with ratings have been kept, sizing the dataset down to 2356 rows. 
<i>Note: the extraction has been done by the Udacity’s teacher, and given to me as is. The extraction was far from perfect, and assessing and cleaning of these column are necessary.</i>

<b>Additional Data via the Twitter API.</b>
Retweet count and favorite count are not included in the original WeRateDogs Twitter archive. Additional gathering will have to be done from Twitter’s API, using the tweet ID’s found in the archive. 

<b>Image Predictions File.</b>
Every image in the WeRateDogs Twitter archive has been ran through a neural network that can classify breeds of dogs. The resulting dataframe is a table with the top three image predictions, alongside each tweet ID, image URL and the image number that corresponded to the most confident prediction (numbered 1 to 4 since tweets can have up to four images).
-	P1 is the algorithm’s #1 prediction for the image in the tweet.
-	P1_conf is how confident the algorithm is in its #1 prediction.
-	P1_dog is whether or not the #1 prediction is a breed of dog. (True or False)
-	P2 is the algorithm’s second most likely prediction.
-	P2_conf is how confident the algorithm is in its #2 prediction.
-	P2_dog is whether or not the #2 prediction is a breed of dog. (True or False)
-	Etc. 
<i>Note: This file and this neural network have not been created/made by me, but given to me as is by an Udacity teacher.</i>

## Step 1: Gathering Data<a name="gathering"></a> 

Gather all three pieces of data. The methods required to gather each data are different.
-	WeRateDogs Twitter archive. Downloaded manually by clicking this link: <a href="https://d17h27t6h515a5.cloudfront.net/topher/2017/August/59a4e958_twitter-archive-enhanced/twitter-archive-enhanced.csv">twitter_archive_enhanced.csv</a>. Once downloaded, it is uploaded and read into a pandas DataFrame

-	The tweet image predictions. Downloaded programmatically using the Requests library and : <a href="https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv">this URL</a>.

-	Additional data from the Twitter API. Gather each tweet’s retweet count and favorite (‘like’) count. Using the tweet IDs in the WeRateDogs Twitter archive, I’ve queried the twitter API for each tweet’s JSON data using Python’s tweepy library and stored each tweet’s entire set of JSON data in a file called tweet_json.txt. Then I’ve read this .txt file line by line into a Pandas DataFrame. Note: My Twitter API keys, secrets and token will not be included in this project.

## Step 2: Assessing Data<a name="assessing"></a>   

After gathering all three pieces of data, I assessed them visually and programmatically for quality and tidiness issues. I was tasked with detecting and documenting at least eight quality issues and two tidiness issues. 
To meet specifications, the following had to be assessed:
-	We only wanted original ratings (no retweets). Not every tweets are dog ratings and some are retweets.
-	Assessing and cleaning the entire dataset completely would require a lot of time, and is not necessary to practice and demonstrate my skills in data wrangling. 
-	The fact that the rating numerators are greater than the denominators did not need to be cleaned. This unique rating system is a big part of the popularitu of WeRateDogs.
-	I wasn’t tasked with gathering the tweets beyond August 1st, 2017. Since the algorithm used for the image predictions dataset is not available to me, I’ve had to limit myself to what was accessible. 

## Step 3: Cleaning Data<a name="cleaning"></a> 

Cleaned all of the issues I documented while assessing. I was asked to: make a copy of the original data before performing any cleaning tasks, use a the define-code-test framework and clearly document it. Merge individual pieces of data to end up with a high quality and tidy master pandas DataFrame.

## Step 4: Storing Data<a name="storing"></a>
  
Stored the cleaned master datafame in a CSV file named twitter_archive_master.csv.

## Step 5: Analyzing and Visualizing Data<a name="analyzing"></a>

Produced at least three insights and one visualization. 

