---
title: Sparkify - Churn Analysis
author: ''
date: '2021-12-28'
slug: sparkify-churn-analysis
categories: []
tags: []
description: Desc
hacker_news_id: ''
lobsters_id: ''
meta_img: /images/image.jpg
---
![](/post/2021-11-28-sparkify-churn-analysis_files/music.jpeg)
<sub>credit:unsplash.com</sub>

# Sparkify Goal
Sparkify corp tracks Monthly Acitve User(MAU) as its flagship metric. To keep MAU growing it needs to acquire new users and reduce churn(keep the existing users happy without cancelling the subsciption and leaving the platform). Reducing the churn will improve revenue through premium  from subscription users and ad ad revenues played to free and premuium subscribers.

# Objective of Model
Aim is to predict the users who are most like to churn. so, we can incentivize them to stay in the platform. 

# Evaluation metric:
AUC is the evaluation metric and performs better than accuracy and F1 for imbalanced data set. Area Under Curve(AUC) is the measure of how well the classifier is classfing the churn and not churn users. This is arrived as area of probability curve plotting True Positive Rates(TPR) against False Postive Rates(FPR). <br>
Higher the AUC better the abiliyt of model to classify positive and negative. If AUC=1, Classifier perfectly classifies both the classes. If AUC=0, Classifier is as good as random prediction. If AUC=0, Classifier predicts accurately incorrectly( inverting the prediction will help us in achieve our result)

# Data Scope:
Session details with their actions of 22k users are provided for time period between 2018-10-01 and 2018-12-01. A user is marked as Churn if the user had cancelled his membership with Sparkify(tracked through Cancellation confirmation page).


# Data Quality:
Null values in Registraion and userId are dropped for this exercise.Timestamps areconverted to date values.


# Data observations
Dataset had 26.25 million rows of user session logs amouting to 12.5 GB making it feasible to group and summarise only in a dsitributed environment Spark. Total number of users is 22,277. 22%(5003 users) had churned.Obsdays are exlcuded from the dataset as they may cause data leakage as most of the churned user will not have observations for complete duration and would have left midway.

# Base model
Baseline model used is logistic regression with mean AUC of 0.55. Running a untuned xgboost model yields mean AUC = 0.989. Hyperparameter tuning is done with optuna.

# Final model and hyperparameter optimasatoin
Final model yields mean AUC of 
Important features are explained using SHAP package. Features nDowngrade and registDuration come out to be more important features. nDowngrade and 
registDuration points to problems in our recommendation engine and new user experience respectively.

# Further Improvements
* Additional Dataset on music taste and liked artists can help us to naill down the perfect music catalogue




