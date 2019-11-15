---
layout: post
title: "Duplicate questions on Quora"
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

Additionally we find out the number of unique questions in the data set and number of questions which are repeated. This is important as this will help us in feature engineering which will be done in the next section. 

<img width="623" alt="Screen Shot 2019-11-15 at 2 53 47 PM" src="https://user-images.githubusercontent.com/16144527/68932061-d5775a80-07b7-11ea-965e-e04ff7f7e475.png">





_The end_

