---
layout: post
title: "Detecting Duplicate Questions on Quora"
author: "Pawan Bharadwaj"
---

Quora is a social media platform where knowledge sharing happens via questions and answers. Nearly 100 million people visit the website every month so there are lot of questions and answers being shared on that website, which brings in a unique problem of duplicate questions, i.e same questions being asked by different people. It's very important for Quora to eliminate the duplicate questions and provide a better experience for people who are seeking answers and those who are putting in effort to write them. In this we will find out how this was solved. First we define the problem statement. 

# Problem Statement and Constraints: 
The basic task is to identify which quesions asked on Quora are duplicates of questions already asked. We will have to predict whether a pair of questions are questions are duplicate or not. We have to realise that the cost of misclassification is very high and that's we need to be set thresholds for the probability of pair of questions being duplicate. 

Before we jump into understanding the data, we need to understand what kind of machine learning problem we will be working on. Knowing this will give us a clear goal to work on. Since we will only be prediction if a question is duplicate or not,our output variable will be (Y) either 0's or 1's. Because of this it becomes a simple binary classification problem. 
But our final aim is not to  just have 0's and 1's but to have a probability value with which we can tell if the questions are duplicate or not. So for that we will be using log loss method as the performance metric for our classification problem. We also have another performance metric called Binary Confsion matrix which I will be explaining later but thisi is another metric which will give us more insights into our solution. 

# Exploratory Data Analysis

The data for this particualr problem was taken from the kaggle's competetion website (https://www.kaggle.com/c/quora-question-pairs/data). Before we jump into feautre engineering and basics of natural languange processing. We will performing basic statistics on the data to have a better understanding of the problem and if there are any anomolies in the data we can remove them. 

From  the below image we see that there are six columns. First column is a normal row ID while the second and third columns are unique ID's of each question of the pair of questions. The third and fourth column are the questions itself whilethe last column is target variable or label we will be trying to predict they have either 0's or 1's as it's values. 

<img width="835" alt="Screen Shot 2019-11-10 at 8 01 08 PM" src="https://user-images.githubusercontent.com/16144527/68546051-f5460180-03f8-11ea-8e8c-550fcd729975.png">

We then get more information about the data points like number of question pairs for training and how many similar and non similar question are there in our data set. 

<img width="936" alt="Screen Shot 2019-11-15 at 2 42 06 PM" src="https://user-images.githubusercontent.com/16144527/68931340-52093980-07b6-11ea-9368-589d271247d0.png">

Additionally we find out the number of unique questions in the data set and number of questions which are repeated. This is important as this will help us in feature engineering which will be done in the next section. As we see from the graph below the number of unique questions are quite high but to be precise the total  number of unique Questions are 537933
while Unique questions which are repeated are around 111780 that's approximately 20% of our data set. 


<img width="623" alt="Screen Shot 2019-11-15 at 2 53 47 PM" src="https://user-images.githubusercontent.com/16144527/68932061-d5775a80-07b7-11ea-965e-e04ff7f7e475.png">


# Feature extraction 

We will be doing some basic feature extraction where in we create some new columns(features) in our data set and see if they are useful in the classification of the data set which was out initial goal to begin with. After few iteration to create fewatures we see that only few are useful in getting insight. 
Here are the features we will be creating to have some insights into our data set. 

  q1_n_words = Number of words in Question 1
  q2_n_words = Number of words in Question 2
  words_common = (Number of common unique words in Question 1 and Question 2)
  words_total =(Total num of words in Question 1 + Total num of words in Question 2)
  words_shared = (word_common)/(word_Total)
  
The following code is used to create the fewatures which will analyse them a little next. 


<img width="581" alt="Screen Shot 2019-11-15 at 4 01 46 PM" src="https://user-images.githubusercontent.com/16144527/68936828-4e2ee480-07c1-11ea-9fc4-57116ddca1db.png">

First we will analyse the word_share feature. This feature was created by finding the common words and the dividing them by total no of words in both the questions. 


<img width="746" alt="Screen Shot 2019-11-15 at 4 22 05 PM" src="https://user-images.githubusercontent.com/16144527/68939501-c8ae3300-07c6-11ea-8612-0561182ecd77.png"> 

<img width="732" alt="Screen Shot 2019-11-15 at 4 22 30 PM" src="https://user-images.githubusercontent.com/16144527/68939506-cba92380-07c6-11ea-82dc-b294195aa1f6.png">

We have plotted a distritubution plot of the feature among class 0's and class 1's. What we observe is that both the distributions overlap a lot and but they don't overlap completely making it very difficult for us to classify them. While this is not the best casescenario, this is something we can work on. In class 1 we see more word shared which indicates that if there are more word shared between questions, the probability of the pair to be similar is quite high. Same way we see that word shared in class 0 label is not high indicating an observation similar previous one. Having said that we need to do futher feature extraction for us to have even clearer method for classifying the class labels. 

# Feature Extraction with TF-IDF
The first thing to do is to find the TF-IDF scores which we will be using to convert each question to weighted average of word2vec vectors. The following code is used for getting the Tf-idf scores 

<img width="497" alt="Screen Shot 2019-11-15 at 5 26 24 PM" src="https://user-images.githubusercontent.com/16144527/68942028-702e6400-07cd-11ea-9e27-29c8490d0702.png">

We use pre trained GLOVE model which was trained on Wikipedia so the word semantics is quite strong in this. We get this model from spacy.io and convert each question to weighted average of word2vec vectors. 

<img width="477" alt="Screen Shot 2019-11-15 at 5 41 37 PM" src="https://user-images.githubusercontent.com/16144527/68942712-44ac7900-07cf-11ea-8771-b369a5cba4a8.png"> 

The above code is for the first questions in a pair and the code below is for the second questions in the question pair. 

<img width="477" alt="Screen Shot 2019-11-15 at 5 41 37 PM" src="https://user-images.githubusercontent.com/16144527/68942712-44ac7900-07cf-11ea-8771-b369a5cba4a8.png">

Using this we will create features which comes to 794 features, so we will training a model with 790 dimensions. The code for the same is given below. We create a new csv file so that we can use that for training it on our models. 

<img width="858" alt="Screen Shot 2019-11-15 at 6 08 38 PM" src="https://user-images.githubusercontent.com/16144527/68944088-05802700-07d3-11ea-91e7-28a7100ed22c.png">

# Training- Test Data Split 
We randomly split the date in terms of 70:30 meaning 70% is trianing data while 30% is ourtest data
It's a simple one line code for doing this. If we had more information like for example time stamp of the questions asked, we can split the data based on the time stamp but since we dont have any additional information, we do a random split. 

<img width="767" alt="Screen Shot 2019-11-15 at 6 14 57 PM" src="https://user-images.githubusercontent.com/16144527/68944585-25641a80-07d4-11ea-8ba9-083319448b55.png">


# ML Modeling: XGBoost

After trying different linear models and non linear models, it was decided that XG boost gives best results in terms of log loss in training and test data. 

<img width="727" alt="Screen Shot 2019-11-15 at 6 18 49 PM" src="https://user-images.githubusercontent.com/16144527/68944734-97d4fa80-07d4-11ea-8032-7a13ac243b5f.png">

<img width="449" alt="Screen Shot 2019-11-15 at 6 19 10 PM" src="https://user-images.githubusercontent.com/16144527/68944785-c18e2180-07d4-11ea-95dd-b480907fb385.png">

We see that the log loss of train and test data are quite similar. This gives us some indication that there is not much overfitting and in XG boost changes of underfitting is quite low. 

We will check the binary confusion matrix for futher insight and we see that the precision for predicting the first class is quite high while linear models dont perform this well. 

<img width="938" alt="Screen Shot 2019-11-15 at 6 19 17 PM" src="https://user-images.githubusercontent.com/16144527/68944799-c94dc600-07d4-11ea-917f-23352f48ea84.png">

