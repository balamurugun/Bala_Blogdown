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
Sparkify corp tracks Monthly Active User(MAU) as its flagship metric. To keep MAU growing it needs to acquire new users and reduce churn(keep the existing users happy without leaving the platform). Reducing the churn will improve revenue through premium from subscription users and ad revenues played to free and premium subscribers.

# Objective of Model
The aim of the model is to predict the users who are expected to churn based on their behaviour. So, we can incentivize them to stay on the platform
* Access the session log details of the users
* Clean the data to remove null users Ids and null Registration
* Summarise the user behaviour and create new features
* Visualise the user behaviour
* Build a baseline model and tune the hyperparameters to arrive the best performing final model based on the evaluation metrics AUC

Code-behind this analysis can be found in  [Github](https://github.com/in-balamurugan/sparkify_user_churn)


# Evaluation metric:
AUC is the evaluation metric and performs better than accuracy and F1 for the imbalanced data set. Area Under Curve(AUC) is the measure of how well the classifier is classifying the churn and not churn users. This arrives as the area of probability curve plotting True Positive Rates(TPR) against False Positive Rates(FPR). <br>
Higher the AUC better the ability of the model to classify positive and negative. If AUC=1, the classifier perfectly classifies both the classes. If AUC=0, Classifier is as good as random prediction. If AUC=0, the Classifier predicts accurately incorrectly( inverting the prediction will help us in achieving our result)

# Data Scope:
Session details with the actions of 22k users are provided for tge time period between 2018-10-01 and 2018-12-01. A user is marked as Churn if the user had cancelled his membership with Sparkify(tracked through the Cancellation confirmation page).


# Data Quality:
Null values in Registration and userId are dropped for this exercise. Timestamps are converted to date values.


# Data observations
Dataset had 26.25 million rows of user session logs amounting to 12.5 GB making it feasible to the group and summarise only in a distributed environment Spark. The total number of users is 22,277. 22%(5003 users) had churned. Obsdays are excluded from the dataset as they may cause data leakage as most of the churned users will not have observations for the complete duration and would have left midway.

![](/post/2021-11-28-sparkify-churn-analysis_files/churned_users.png)

#Hyperparameter Optimisation
Hyperparameter is performed on XGBoost model through framework Optuna.
Here are the  parameters and ranges teseted:
* max_depth (1 to 9)
* min_child_weight (2 to 10)
* eta aka learning rate (1e-8 to 1)
* gamma (1e-8 to 1)
  
# Base model
Below is a summary of all modesl
![](/post/2021-11-28-sparkify-churn-analysis_files/summary.png)

# Final model 
Final model yields a mean AUC of 0.97.
Important features are explained using SHAP package. Features nSongs and avgDailyDowngrade come out to be more important features.A user who listened to fewer songs and downgraded from paid tier to free tier is most likely to churn.
![](/post/2021-11-28-sparkify-churn-analysis_files/imp_features.png)

# Summary
The Model helps to find out users expected to churn and incentivize them to stay back with platform.

# Further Improvements
* Additional Dataset on music taste and liked artists can help us to naill down the perfect music catalog.

# Challenges
* Dataset time period is short so tough to test out how it will hold on real-world.

# Credits
* Udacity
* Book: Approaching Almost Any Machine learning problem