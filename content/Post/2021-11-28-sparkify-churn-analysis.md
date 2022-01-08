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

# Project Overview
Sparkify is a music streaming company. Sparkify tracks Monthly Active User(MAU) as its flagship metric. To keep MAU growing it needs to acquire new users and reduce churn(keep the existing users happy without leaving the platform). Reducing the churn will improve revenue through premium and ad revenues.

# Problem Statement
The goal of the project is to predict the users who are expected to churn based on their behaviour. So, we can incentivize them to stay on the platform
* Access the session log details of the users
* Clean the data to remove null users Ids and null Registration
* Summarise the user behaviour and create new features
* Visualise the user behaviour
* Build a baseline model and tune the hyperparameters to arrive the best performing final model based on the evaluation metrics AUC

Code-behind this analysis can be found in  [Github](https://github.com/in-balamurugan/sparkify_user_churn)

# Evaluation metric
AUC is the evaluation metric and performs better than accuracy and F1 for the imbalanced data set. Area Under Curve(AUC) is the measure of how well the classifier is classifying the churn and not churn users. This arrives as the area of probability curve plotting True Positive Rates(TPR) against False Positive Rates(FPR). <br>
Higher the AUC better the ability of the model to classify positive and negative. If AUC=1, the classifier perfectly classifies both the classes. If AUC=0, Classifier is as good as random prediction. If AUC=0, the Classifier predicts accurately incorrectly( inverting the prediction will help us in achieving our result).
<br>AUC is a widely used metric for skewed binary classification tasks in the industry. Suppose model AUC is 0.95, this means that if you select a random user who has churned and another user who has not churned, then the churned user will rank higher
than a non-churned with a probability of 0.95.

# Data Exploration
Session details with the actions of 22k users are provided for tge time period between 2018-10-01 and 2018-12-01. A user is marked as Churn if the user had cancelled his membership with Sparkify(tracked through the Cancellation confirmation page).
Here are the columns included in the session log:

* artist
* auth
* firstName
* gender
* itemInSession
* lastName
* length
* level
* location
* method
* page
* registration
* sessionId
* song
* status
* ts
* userAgent
* userId

Observation period is between 2018-10-01 and 2018-12-01.Dataset had 26.25 million rows of user session logs amounting to 12.5 GB making it feasible to the group and summarise only in a distributed environment Spark. 


# Data preprocessing
Null values in Registration and null userIda are dropped for this exercise. Timestamps are converted to date values.User sessions are summarised and converted into table of users with following features. Here are the new features created for each user.

* Churn
* obsDays
* nSongs
* nThumbsUp
* nThumbsDown
* nUpgrade
* nDowngrade
* nAddFriend
* nAddPlaylist
* nAdvert
* nHelp
* nError
* registDuration
* avgSessionDuration
* avgDailySongs
* avgDailyThumbsUp
* avgDailyThumbsDown
* avgDailyUpgrade
* avgDailyDowngrade
* avgDailyAddFriend
* avgDailyAddPlaylist
* avgDailyAdvert
* avgDailyHelp
* avgDailyError

# Data visualisation
The total number of users is 22,277. 22%(5003 users) had churned. Obsdays are excluded from the dataset as they may cause data leakage as most of the churned users will not have observations for the complete duration and would have left midway.

![](/post/2021-11-28-sparkify-churn-analysis_files/churned_users.png)

avgDailySongs for non churned users is 3x greater than churned users.
![](/post/2021-11-28-sparkify-churn-analysis_files/average_songs.png)

However, session duration is lower a for churned users.
![](/post/2021-11-28-sparkify-churn-analysis_files/session_duraiton.png)

# Model Implementation, Evaluation and Validation
Model is evaluated using AUC metric on different algorithms. User list is split into stratified five folds to check the various models robustness on cross validated data. So, 80% data is train data and 20% is validation data.
Logistic regresion is tried out as baseline model on all five folds and mean AUC metric is 0.87. Next Random forest is implement with default parameters with mean AUC metric is 0.93. XG Boost yields a low 0.64. However, when we proceed to tune the hyperparameter using Optuna and rerun the XGBoost model, we end up with a good AUC of 0.97.
Below is a summary of all modesl
![](/post/2021-11-28-sparkify-churn-analysis_files/summary.png)


# Hyperparameter Optimisation
Hyperparameter is performed on XGBoost model through framework Optuna.
Here are the  parameters and ranges teseted:
* max_depth (1 to 9)
* min_child_weight (2 to 10)
* eta aka learning rate (1e-8 to 1)
* gamma (1e-8 to 1)

# Refinement
Algorithms are progressively applied on the dataset from Logistic regression, Random forester, XGBoost and finally tuned XGBoost.
Also realsied during the model training, using number of observationd days as a feature made the model to learn if obs_days=60,then the user is non-churned and less than 60 for churned users. This feature is now dropped and trained preventing data leakage.

# Final model 
Final model yields a mean AUC of 0.97.
Important features are explained using SHAP (SHapley Additive exPlanations) package. A mdoel inference on most important features is done through python package .Features nSongs and avgDailyDowngrade come out to be more important features.A user who listened to fewer songs and downgraded from paid tier to free tier is most likely to churn.
![](/post/2021-11-28-sparkify-churn-analysis_files/imp_features.png)

# Summary
User session log input is turned into aggregate and average features for each user in spark after preprocessing.User list is then split into various folds and trained on various algorithms with XGBoost tuned paramerers yielding the best resutl.
The Model helps to find out users expected to churn and Saprkify can incentivize them to stay back with platform.

# Further Improvements
* Additional Dataset on music taste and liked artists can help us to naill down the perfect music catalog
* More features can be extracted out of the user listened songs and genre
* Model can be served via a web app

# Challenges
* Dataset time period is short so tough to test out how it will hold on real-world.
* Impossible to fit in local memory so one of the constraints is to fit 
* Building and training the model in AWS EMR costs around $10 and every re-run from scratch costs additional $2. 

# Credits
* Udacity
* Approaching Almost Any Machine learning problem
* Optuna for hyperparameter training