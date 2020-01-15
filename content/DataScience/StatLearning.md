---
title: StatLearning with Zero Code and Equation
author: ''
date: '2019-07-23'
slug: StatLearning
categories: []
tags: []
description: Desc
hacker_news_id: ''
lobsters_id: ''
meta_img: /images/image.jpg
---

My aim over this course is to provide notes on course Stastical Learning with no code or equation.

Introduction to Regression models

#Overview of Statistical Learning

Let us set out to predict Salary(Y) based on Experience, Education and Martial Status(really?)(Bunch of Xs)
Regression equation is defined as function of these features plus an error value which is not captured by the model. Bearuty of regression is Obviousoly  to reduce the error rate for any new predction and/or define the existing relation between feature and target.

##Regression Function
Ideal function which gives the exact average of Y at each point of X.
Regression Function aim is to reduce the mean squared error and make prediction to look good. Wait what is Mean Squared Error? Sum of squares of predictions and actuals.

In few words, Regression Function is the ideal/optimal predictor of Y.

###Irreducible Error, called Epsilons
Since for same X, multiple Y values exists, never Regression function can equal Y. this difference is Ireducible Error.Similar to a manger cant keep all his juniors happy.
But still regression function does good job on average :)

How to compute y when there is no X? copy the average of the neighbour. this is nearest neigbhourhood averaging.


##Curse of Dimensionality
Neighbourhood estiamtes doesnt work well for large dimensions eg: hypercube with 5% boundary has 99% of the points as neighbour.Will be less local as we want to go further

Is this like a student trying to copy answers from too many smart students sitting adjacent but writing different answer to same question?


So how to escape,here comes the linear models. 
Linear models have a coefficient for each predictor and tries provide better fitting.
Quadratic is even better for fit in some cases fro single dimension

Similarly in mutli dimension, thin spline goes through more points than linear model and does over fitting

So trades offs between 
Prediction vs Interpretability, think thin spline vs linear moder
Good fit vs Over fit/under fit

So remeber flexibility vs Interpretability. one end is subset/lasso/linear regression, other end is Bagging/Boosting/SVMs.

###Assessing Model Accuracy
How to find which model is adequate and accurate?
Do a average squared error on the training data. But don. Over fit data can cheat. So do on a fresh test set.

##Bias Variance Trade off
What is flexibility?
Ability to fit to different data. So more Flexibility leads to more variancee.

###Classification
how to measure classifcation effectivness?
Measure average number of mistakes

What is  decision boundry?
Contour where both probabilities are equal

How does base classifier work for KNN?
Draw a circle, average nearest points and go with them. Make k bigger, decision bonray smppht

What is the bias variance trade off for classifiers?

Flexible statistical learning method  is a student who reads too many topics but nothing deep. eg: spline
Non flexible statistical learning method is a student who reads very few topics but deep. eg:Linear regression

#Linear Regression
Linear regression simple but effective 
1) finding the strength
2) predicitng relation

Equation is created to minimize the least square errors, that is the error between actual and estimate at each point


How to measure relation?
check out what the intercepts(beta2) and slope(beta1) are.

What does 95% confidence intervals mean?
Range which contains true value with 95% confidence. so take estimate of slope and twice(1.96) the Standard error(asuuming errors are distributed normally)  


##Hypothesis testing

Also on linear regression, we will be able to t-test whether the relation is significant(p>5%) or not.
T-stastic on intercept says what happens to sales if budget is zero.
T-stastic on intercept says what is the relation between tv budget and sales

Null Hypothesis says Beta2 is  zero, no relation between X and Y
Alternate hypothesis  says B2 is bti zero.But this measures only nonzero association.

How to check the accuracy of the model?
R2(R-squared) is nothing but variance that can be explained with the fitted model.
RSS is square of standard error si the unexplained variance or variance of the model's errors
TSS is total variance of the data
Variance explained is the left over of the proportion of unexplained variance by total variance of the data
R2 als equal simple squared co-relation between variable and predictor.

So, what is a good Rsquared value...depends on the domain




#Multi-Linear Regression
Y = Beta0 +Beta1X1 +Beta2X2+Beta3X3+....
Wrong definition: 
How one varibale predicts the outcome when all other variables are zero

Are there any  usefule indicators explaining the impact on outcome?
check R2 the variance and p value of F stastics

What are the variables to include?
Calculate all possible subsets and pick the best one..kidding p=40 has billion subsets (2^40)
Go to Automate apporach
1) Forward selection
2) Backward selection - Remove leadt significant

##How to model qualitiative predictors?
For K levles, add k-1 dummy variables with a baseline.
RSS of the model doesnt change based on baseline however p value changes.

##Interaction
How to find out 







  
















