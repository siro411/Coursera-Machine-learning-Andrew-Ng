# Linear Regression with One Variable
> Q1:<br>Consider the problem of predicting how well a student does in her second year of college/university, given how well she did in her first year.

>Specifically, let x be equal to the number of "A" grades (including A-. A and A+ grades) that a student receives in their first year of college (freshmen year). We would like to predict the value of y, which we define as the number of "A" grades they get in their second year (sophomore year).

>Here each row is one training example. Recall that in linear regression, our hypothesis is h_θ(x)=θ_0+θ_1*x,and we use **m** to denote the number of training examples.

x | y
:--- |:---
3 | 2
1 | 2
0 | 1
4 | 3

>For the training set given above (note that this training set may also be referenced in other questions in this quiz), what is the value of mm? In the box below, please enter your answer (which should be a number between 0 and 10).

A:
- 4

> Q2:<br>For this question, assume that we are using the training set from Q1. Recall our definition of the cost function was J(θ_0,θ_1)=![](https://latex.codecogs.com/png.latex?\inline&space;\bg_white&space;{\frac{1}{2m}}\sum_{i=1}^{m}\left&space;(&space;h_\theta(x^{(i)})-y^{(i)}&space;\right&space;)^2).What is J(0, 1)J(0,1)? In the box below,please enter your answer (Simplify fractions to decimals when entering answer, and '.' as the decimal delimiter e.g., 1.5).
- When θ_0=0 and θ_1=1, we have h_θ(x)=θ_0+θ_1x=x. So, J(θ_0,θ_1)=1/(2*4)*(1+1+1+1)=0.5

> Q3:<br>Suppose we set θ_0 = -2, θ_1 = 0.5 in the linear regression hypothesis from Q1. What is h_θ(6)?
- Setting x = 6, we have hθ(x)=θ_0+θ_1x=-2+0.5*6=1

>Q4:<br>
Let f be some function so that f(θ_0,θ_1) outputs a number. For this problem, f is some arbitrary/unknown smooth function (not necessarily the cost function of linear regression, so f may have local optima). Suppose we use gradient descent to try to minimize f(θ_0,θ_1) as a function of θ_0 and θ_1. Which of the following statements are true? (Check all that apply.)

A:
> - [ ] Setting the learning rate to be very small is not harmful, and can only speed up the convergence of gradient descent.
> - [x] If θ0 and θ1 are initialized at a local minimum, then one iteration will not change their values.
> - [ ] No matter how θ0 and θ1 are initialized, so long as learning rate is sufficiently small, we can safely expect gradient descent to converge to the same solution
> - [x] If the first few iterations of gradient descent cause f(θ0,θ1) to increase rather than decrease, then the most likely cause is that we have set the learning rate to too large a value
> - [x] If the learning rate is too small, then gradient descent may take a very long time to converge.
> - [ ] Even if the learning rate α is very large, every iteration of gradient descent will decrease the value of f(θ0,θ1).
> - [ ] If θ0 and θ1 are initialized so that θ0=θ1, then by symmetry (because we do simultaneous updates to the two parameters), after one iteration of gradient descent, we will still have θ0=θ1.

>Q5:<br>
Suppose that for some linear regression problem (say, predicting housing prices as in the lecture), we have some training set, and for our training set we managed to find some θ0, θ1 such that J(θ0,θ1)=0.

Which of the statements below must then be true? (Check all that apply.)
A:
> - [ ] For this to be true, we must have y(i)=0 for every value of i=1,2,…,m.
> - [ ] Gradient descent is likely to get stuck at a local minimum and fail to find the global minimum.
> - [ ] For this to be true, we must have θ0=0 and θ1=0 so that hθ(x)=0
> - [x] Our training set can be fit perfectly by a straight line, i.e., all of our training examples lie perfectly on some straight line.
> - [ ] We can perfectly predict the value of y even for new examples that we have not yet seen. (e.g., we can perfectly predict prices of even new houses that we have not yet seen.)
> - [ ] This is not possible: By the definition of J(θ0,θ1), it is not possible for there to exist θ0 and θ1 so that J(θ0,θ1)=0
> - [x] For these values of θ0 and θ1 that satisfy J(θ0,θ1)=0, we have that hθ(x(i))=y(i) for every training example (x(i),y(i)). 
