<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>

# Introduction
## What is Machine Learning?
Two definitions of Machine Learning are offered. 
>Arthur Samuel described it as: "the field of study that gives computers the ability to learn without being explicitly programmed." This is an older, informal definition.<br>
Tom Mitchell provides a more modern definition: "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."

Example: playing checkers.

E = the experience of playing many games of checkers

T = the task of playing checkers.

P = the probability that the program will win the next game.

In general, any machine learning problem can be assigned to one of two broad classifications:

Supervised learning and Unsupervised learning.

Q: 
>"A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E."

Suppose your email program watches which emails you do or do not mark as spam, and based on that learns how to better filter spam. What is the task T in this setting?

A:
> - [x] **Classify emails as spam or not spam.**
> - [ ] Watching you label emails as spam or not spam.
> - [ ] The number (or fraction) of emails correctly classified as spam/not spam.
> - [ ] None of the above, this is not a machine learning algorithm.
------
## Supervised Learning

In supervised learning, we are given a data set and already know what our correct output should look like, having the idea that there is a relationship between the input and the output.

Supervised learning problems are categorized into "regression" and "classification" problems. In a regression problem, we are trying to predict results within a continuous output, meaning that we are trying to map input variables to some continuous function. In a classification problem, we are instead trying to predict results in a discrete output. In other words, we are trying to map input variables into discrete categories.

Q: <br>
You’re running a company, and you want to develop learning algorithms to address each of two problems. 
>Problem 1:You have a large inventory of identical items. You want to predict how many of these items will sell over the next 3 months.<br>
Problem 2: You’d like software to examine individual customer accounts, and for each account decide if it has been hacked/compromised. Should you treat these as classification or as regression problems?

A:
> - [ ] Treat both as classification problems.
> - [ ] Treat problem 1 as a classification problem, problem 2 as a regression problem.
> - [x] **Treat problem 1 as a regression problem, problem 2 as a classification problem.**
> - [ ] Treat both as regression problems.
------
## Unsupervised Learning

Unsupervised learning allows us to approach problems with little or no idea what our results should look like. We can derive structure from data where we don't necessarily know the effect of the variables.

We can derive this structure by clustering the data based on relationships among the variables in the data.

With unsupervised learning there is no feedback based on the prediction results.

Q:<br>
Of the following examples, which would you address using an unsupervised learning algorithm? (Check all that apply.)

A:
> - [ ] Given email labeled as spam/not spam, learn a spam filter.
> - [x] Given a set of news articles found on the web, group them into sets of articles about the same stories.
> - [x] Given a database of customer data, automatically discover market segments and group customers into different market segments.
> - [ ] Given a dataset of patients diagnosed as either having diabetes or not, learn to classify new patients as having diabetes or not.

------
# Linear Regression with One Variable
## Model Representation

To describe the supervised learning problem slightly more formally, our goal is, given a training set, to learn a function h : X → Y so that h(x) is a “good” predictor for the corresponding value of y. For historical reasons, this function h is called a hypothesis. Seen pictorially, the process is therefore like this:

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/H6qTdZmYEeaagxL7xdFKxA_2f0f671110e8f7446bb2b5b2f75a8874_Screenshot-2016-10-23-20.14.58.png?expiry=1580601600000&hmac=xgyCO3Kgw8eA_c9D0qSuZ5ZeHAT0TYPOQjAN6IfVi48)

Q:<br>
Consider the training set shown below. (x<sup>(i)</sup>, y<sup>(i)</sup>) is the i<sup>th</sup> training example. What is y<sup>(3)</sup> ?
Size in feet<sup>2</sup>(x)  | Price ($) in 1000's (y)
------------- | -------------
2104  | 460
1416  | 232
1534  | 315
852  | 178
...  | ...

A:
> - [ ] 1416 
> - [ ] 1534 
> - [x] 315 
> - [ ] 0 

------
## Cost function
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/R2YF5Lj3EeajLxLfjQiSjg_110c901f58043f995a35b31431935290_Screen-Shot-2016-12-02-at-5.23.31-PM.png?expiry=1580601600000&hmac=Eg4yLxBu6GA7Yt5ZOvN19RZOY3EFf6gWFnPg15WVjYQ)

Q:<br>
Consider the plot below of $$h_\theta(x)= \theta_0 +\theta_1x$$.What are  $$\theta_0$$ and $$\theta_1$$? 

![](https://spark-public.s3.amazonaws.com/ml/images/2.2-quiz-1-fig.jpg)

A:<br>
> - [ ] $$\theta_0$$ =0, $$\theta_1$$ =1
> - [x] $$\theta_0$$ =0.5, $$\theta_1$$ =1 
> - [ ] $$\theta_0$$ =1, $$\theta_1$$ =0.5
> - [ ] $$\theta_0$$ =1, $$\theta_1$$ =1 

------
## Cost function Intuition I
Suppose we have a training set with m=3 examples, plotted below. Our hypothesis representation is $$h_\theta(x)=\theta_1x$$.with parameter $$\theta_1$$. The cost function $$J(\theta_1)$$ is $$J(\theta_1$$=
![](https://latex.codecogs.com/png.latex?\inline&space;\bg_white&space;{\frac{1}{2m}}\sum_{i=1}^{m}\left&space;(&space;h_\theta(x^{(i)})-y^{(i)}&space;\right&space;)^2).What is J(0)?

![](https://spark-public.s3.amazonaws.com/ml/images/2.3-quiz-1-fig.jpg)

> - [ ] 0
> - [ ] 1/6
> - [ ] 1
> - [x] 14/6

-----
## Cost function Intuition II


![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/N2oKYp2wEeaVChLw2Vaaug_d4d1c5b1c90578b32a6672e3b7e4b3a4_Screenshot-2016-10-29-01.14.37.png?expiry=1580601600000&hmac=o9lxXxnEBvaCPXKWgu6RkkTvZLwDgcwFevfSZaWUUlU)