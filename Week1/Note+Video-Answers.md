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
:------------ | :------------
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
Consider the plot below of h_θ(x)= θ_0 +θ_1*x.What are  θ_0 and θ_1? 

![](https://spark-public.s3.amazonaws.com/ml/images/2.2-quiz-1-fig.jpg)

A:<br>
> - [ ] θ_0 =0, θ_1 =1
> - [x] θ_0 =0.5, θ_1 =1 
> - [ ] θ_0 =1, θ_1 =0.5
> - [ ] θ_0 =1, θ_1 =1 

------
## Cost function Intuition I
Suppose we have a training set with m=3 examples, plotted below. Our hypothesis representation is h_θ(x)=θ_1x$$.with parameter θ_1. The cost function J(θ_1) is J(θ_1)=
![](https://latex.codecogs.com/png.latex?\inline&space;\bg_white&space;{\frac{1}{2m}}\sum_{i=1}^{m}\left&space;(&space;h_\theta(x^{(i)})-y^{(i)}&space;\right&space;)^2).What is J(0)?

![](https://spark-public.s3.amazonaws.com/ml/images/2.3-quiz-1-fig.jpg)

> - [ ] 0
> - [ ] 1/6
> - [ ] 1
> - [x] 14/6

-----
## Cost function Intuition II


![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/N2oKYp2wEeaVChLw2Vaaug_d4d1c5b1c90578b32a6672e3b7e4b3a4_Screenshot-2016-10-29-01.14.37.png?expiry=1580601600000&hmac=o9lxXxnEBvaCPXKWgu6RkkTvZLwDgcwFevfSZaWUUlU)

# Parameter Learning
## Gradient Descent
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/bn9SyaDIEeav5QpTGIv-Pg_0d06dca3d225f3de8b5a4a7e92254153_Screenshot-2016-11-01-23.48.26.png?expiry=1580601600000&hmac=P3lzkyAgd_vbFVTA5XzbAliePAlu7-m6HkrC0o1XL8U)

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/yr-D1aDMEeai9RKvXdDYag_627e5ab52d5ff941c0fcc741c2b162a0_Screenshot-2016-11-02-00.19.56.png?expiry=1580601600000&hmac=VlqY5RCRMkAH1sg23SDJGKHlxsHCwZrTVt2lQWeT8GI)

Q:<br>
Suppose θ_0=1,θ_1=2,and we simultaneously update θ_0 and θ_1 using the rule: θ_j:=θ_j+sqrt(θ_0*θ_1) (for j = 0 and j=1) What are the resulting values of θ_0 and θ_1?

A:
> - [ ] θ_0=1,θ_1=2
> - [x] θ_0=1+sqrt(2),θ_1=2+sqrt(2)
> - [ ] θ_0=2+sqrt(2),θ_1=1+sqrt(2)
> - [ ] θ_0=1+sqrt(2),θ_1=2+sqrt((1+sqrt(2))*2)

## Gradient Descent Intuition
How does gradient descent converge with a fixed step size α?

The intuition behind the convergence is that ![](https://latex.codecogs.com/png.latex?\inline&space;\bg_white&space;\frac{\mathrm{d}&space;}{\mathrm{d}&space;\theta_1}J(\theta_1)) approaches 0 as we approach the bottom of our convex function. At the minimum, the derivative will always be 0 and thus we get:
θ_1:=θ_1-α*0

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/RDcJ-KGXEeaVChLw2Vaaug_cb782d34d272321e88f202940c36afe9_Screenshot-2016-11-03-00.06.00.png?expiry=1580601600000&hmac=yHE16YhLsazxvvWUQyjKZqfU-B0uj1Y9syDF_FQmIBI)

Q:<br>
Suppose θ_1 is at a local optimum of J(θ_1), such as shown in the figure.What will one step of gradient descent ![](https://latex.codecogs.com/png.latex?\inline&space;\bg_white&space;\theta_1&space;:=\theta_1-\alpha&space;\frac{\mathrm{d}&space;}{\mathrm{d}&space;\theta_1}J(\theta_1))
![](https://spark-public.s3.amazonaws.com/ml/images/2.6-quiz-1-fig.jpg)

> - [x] Leave θ_1 unchanged
> - [ ] Change θ_1 in a random direction
> - [ ] Move θ_1 in the direction of the global minimum of J(θ_1)
> - [ ] Decrease θ_1
​
-----
## Gradient Descent For Linear Regression
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/QFpooaaaEea7TQ6MHcgMPA_cc3c276df7991b1072b2afb142a78da1_Screenshot-2016-11-09-08.30.54.png?expiry=1580601600000&hmac=qxACiom2kSO7nyeBH69Co_lduj8tAZKxwEQv9PSW2Os)

Q:<br>

Which of the following are true statements? Select all that apply.

A:
> - [ ] To make gradient descent converge, we must slowly decrease α over time.
> - [ ] Gradient descent is guaranteed to find the global minimum for any function J(θ_0, θ_1)
> - [x] Gradient descent can converge even if α is kept fixed. (But α cannot be too large, or else it may fail to converge.)
> - [x] For the specific choice of cost function J(θ_0,θ_1) used in linear regression, there are no local optima (other than the global optimum).