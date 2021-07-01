---
title: 'Data Jungle: Size, Tech and Salary'
author: Balamurugan Periyasamy
date: '2021-06-30'
slug: kaggle-survey
categories: []
tags: []
description: Desc
hacker_news_id: ''
lobsters_id: ''
meta_img: /images/image.jpg
---
![](/post/kaggle-survey_files/carlos-muza-hpjSkU2UYSU-unsplash.jpg)

We are set to explore the Kaggle 2020 survey for insights on what is the difference between working for a large firm vs a small firm, what is the next tech to learn and how can Data Scientists better their salaries.

Table of contents
1
2
3

The first question we are tackling is what are the differences encountered in a large firm vs a small firm in data science?

There is no major difference in the proportion of titles of Kagglers responded to the survey. So, Large and Small firms use the title alike.
![](/post/kaggle-survey_files/title.png)

Choice of computing platform
Local machine is thepreferred choice. Surprisingly one would have expected small firms to be early adopters of Cloud and to keep their fixed costs low. However, Cloud platforms are more prevalent in Large firms than Small firms.

![](/post/kaggle-survey_files/compute.png)

ML Maturity
Large firms have more models in production for more than two years than the small firms and also less percentage have reported not using any ML methods . That being said, most of the small firms would not have existed two years ago and also a good place to start working from scratch in ML as a response to the question "We are exploring ML methods (and may one day put a model into production)" ratio is high in small firms compared to large firms

![](/post/kaggle-survey_files/ML_Maturity.png)


Language Choice 
Python is the leader of the pack everywhere. R and SQL are more popular in large firms but Javascript and C++ are slightly more popular in small firms. This could also mean Small firms may tend to work more on Edge devices compared to large firms.
![](/post/kaggle-survey_files/Language.png)

Second question: What is the future tech to learn? AWS or Google Cloud

Kagglers still recommend Python overwhelmingly to aspiring data scientists followed by R and SQL. Let us jump into analysing the cloud platforms. Amazon and Google are neck to neck in their offerings. When it comes to the computing platform, AWS leads the pack followed by Google Cloud Platform(GCP). Surprisingly, Azure, second in cloud market share, is in distance to AWS and GCP.

![](/post/kaggle-survey_files/cloud.png)

When we take a peek at the cloud product, ML product and ML experiment tool Kagglers wish to learn in the next two years, all point togoogle. It would be no surprise if Google becomes a dominant force in coming years in the data world.

![](/post/kaggle-survey_files/CloudProduct.png)
![](/post/kaggle-survey_files/MLproduct.png)
![](/post/kaggle-survey_files/MLExperiment.png)


Third: What are the factors that influence the salary adjusted for the cost of living?
Rather than converting all to salaries to USD and comparing, I have decided to use the cost of living index to standardise the salaries. Also, the salaries in the lower end tend to be unrealistic. so,the bottom 10 percentile has been removed and this is validated by improved R2.

The obvious factor is the higher the experience, better the salary.
![](/post/kaggle-survey_files/experience.png)

Interestingly UAE comes out with better salaries for data world after the USA. The surprising factor is EUR denominated countries don't find a place in the top five. Excluding the USA, We have rarely observed other top 5 countries topping the salary list in other surveys as they are not adjusted for the cost of living
![](/post/kaggle-survey_files/country.png)

When it comes to languages influencing better salary,C and Matlab top the list. One reason is they could be the top choice for people with high experience as well. Python being common for almost 90% of the survey population hence purely python is not a distinguishing feature anymore.
![](/post/kaggle-survey_files/SalLanguage.png)


Summary:
Want to build something from ML models from scratch? Goto small firms
Are you better off in places with smooth sailing ML models over cloud? Goto large firms
Based on the learning wishes, Google Cloud will be a dominant force in the future.
Want a better cost of living data salary? Head to USA or second best to UAE.
Python is not a major influencer in salaries as it is already widely used. 



   







