# Multivariate Linear Regression
## Multiple Features
> ![](https://latex.codecogs.com/png.latex?\inline&space;\bg_white&space;x_{j}^{i}) =value of feature j in the i th training example<br>
m=the number of training examples<br>
n=the number of features

hθ(x)=θ0+θ1x1+θ2x2+...θnxn

Q: <br>
Size (feet)^2| Number of bedrooms | Number of floors | Age of home (years) | Price ($1000)
------ | ------ | ------| ------| ------
2104 | 5 | 1 | 45 | 460
1416 | 3 | 2 | 45 | 232
1534 | 3 | 2 | 30 | 315
852 | 2 | 1 | 36 | 178
...| ...| ...| ...|...

In the training set above, what is ![](https://latex.codecogs.com/png.latex?\inline&space;\bg_white&space;x_1^{(4)})?

A:
> - [ ] The size (in feet^2)of the 1st home in the training set
> - [ ] The age (in years) of the 1st home in the training set
> - [x] The size (in feet^2) of the 4th home in the training set
> - [ ] The age (in years) of the 4th home in the training set.
------
## Gradient Descent For Multiple Variables
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/MYm8uqafEeaZoQ7hPZtKqg_c974c2e2953662e9578b38c7b04591ed_Screenshot-2016-11-09-09.07.04.png?expiry=1580601600000&hmac=bFcxwDz1qNnQEa_u0H5Xt3t3RpaNY8lJkZ4ys3uTFT4)

Q:<br>
When there are n features, we define the cost function as
J((theta))=(1/2m)*(sum over i=1 to m(((h(theta)(x(i))) - y(i))^2))
For linear regression, which of the following are also equivalent and correct definitions of J(theta)?

A:
> - [x] J((theta))=(1/2m)*(sum over i=1 to m(((theta)Tranpose (x(i)) - y(i))^2))
> - [x] J((theta))=(1/2m)(sum over i=1 to m(((sum over j=0 to n((theta(j)) *(x(i)(j))) - y(i))^2))
> - [ ] J((theta))=(1/2m)(sum over i=1 to m(((sum over j=1 to n((theta(j)) *(x(i)(j))) - y(i))^2))

## Gradient Descent in Practice I - Feature Scaling
We can speed up gradient descent by having each of our input values in roughly the same range. This is because θ will descend quickly on small ranges and slowly on large ranges, and so will oscillate inefficiently down to the optimum when the variables are very uneven.

Two techniques to help with this are feature scaling and mean normalization. Feature scaling involves dividing the input values by the range (i.e. the maximum value minus the minimum value) of the input variable, resulting in a new range of just 1. Mean normalization involves subtracting the average value for an input variable from the values for that input variable resulting in a new average value for the input variable of just zero. 
![](https://latex.codecogs.com/png.latex?\inline&space;\bg_white&space;x_i&space;:=\frac{x_i-u_i}{s_i})
Where μi is the average of all the values for feature (i) and s_i is the range of values (max - min), or s_i is the standard deviation.

Q:<br>
>Suppose you are using a learning algorithm to estimate the price of houses in a city. You want one of your features x_i to capture the age of the house. In your training set, all of your houses have an age between 30 and 50 years, with an average age of 38 years. Which of the following would you use as features, assuming you use feature scaling and mean normalization?

A:
> - [ ] x_i=age of house
> - [ ] x_i=age of house/50
> - [ ] x_i=(age of house-38)/50
> - [x] x_i=(age of house-38)/20

------
## Gradient Descent in Practice II - Learning Rate
Debugging gradient descent. Make a plot with number of iterations on the x-axis. Now plot the cost function, J(θ) over the number of iterations of gradient descent. If J(θ) ever increases, then you probably need to decrease α.

Automatic convergence test. Declare convergence if J(θ) decreases by less than E in one iteration, where E is some small value such as 10−3. However in practice it's difficult to choose this threshold value.
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/FEfS3aajEea3qApInhZCFg_6be025f7ad145eb0974b244a7f5b3f59_Screenshot-2016-11-09-09.35.59.png?expiry=1580601600000&hmac=mX1u88Y41zp-AHGH05nX9AX5xNEf09akeTVNOYuzhj0)

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/rC2jGKgvEeamBAoLccicqA_ec9e40a58588382f5b6df60637b69470_Screenshot-2016-11-11-08.55.21.png?expiry=1580601600000&hmac=VeuzrTe_yD5o7jzGTQGO2duDqP8g3UfrAz-wAcQa1LY)

To summarize:

If α is too small: slow convergence.

If α is too large: ￼may not decrease on every iteration and thus may not converge.

Q:<br>
Suppose a friend ran gradient descent three times, with α=0.01, α=0.1, and α=1, and got the following three plots (labeled A, B, and C):
![](https://spark-public.s3.amazonaws.com/ml/images/4.4-quiz-1-plots.png)
Which plots corresponds to which values of α?

A:
- A is α=0.01, B is α=0.1, C is α=1.
> In graph C, the cost function is increasing, so the learning rate is set too high. Both graphs A and B converge to an optimum of the cost function, but graph B does so very slowly, so its learning rate is set too low. Graph A lies between the two.
------
## Features and Polynomial Regression
Polynomial Regression

Our hypothesis function need not be linear (a straight line) if that does not fit the data well.

We can change the behavior or curve of our hypothesis function by making it a quadratic, cubic or square root function (or any other form).

Q:<br>
Suppose you want to predict a house's price as a function of its size. Your model is hθ(x)=θ0+θ1(size)+θ2*sqrt(size).

Suppose size ranges from 1 to 1000 (feet^2). You will implement this by fitting a model
hθ(x)=θ0+θ1x1+θ2x2
Finally, suppose you want to use feature scaling (without mean normalization).

Which of the following choices for x1 and x2 should you use? (Note: sqrt{1000} ~= 32)
> x1=size/1000 x2=sqrt(size)/32

-----
# Computing Parameters Analytically
## Normal Equation

Gradient descent gives one way of minimizing J. Let’s discuss a second way of doing so, this time performing the minimization explicitly and without resorting to an iterative algorithm. In the "Normal Equation" method, we will minimize J by explicitly taking its derivatives with respect to the θj ’s, and setting them to zero. This allows us to find the optimum theta without iteration. The normal equation formula is given below:

![](https://latex.codecogs.com/png.latex?\inline&space;\bg_white&space;\theta&space;=\left&space;(&space;X^{T}&space;X\right&space;)^{-1}X^{T}y)

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/dykma6dwEea3qApInhZCFg_333df5f11086fee19c4fb81bc34d5125_Screenshot-2016-11-10-10.06.16.png?expiry=1580601600000&hmac=0KQcXUaCJ7sSWEfPjOw9wT-aAjVLr7kuT6lrxzXPkck)

There is no need to do feature scaling with the normal equation.

The following is a comparison of gradient descent and the normal equation:

Gradient Descent	|Normal Equation
---|---
Need to choose alpha	| No need to choose alpha
Needs many iterations	|No need to iterate
O (kn^2) |	O (n^3),need to calculate inverse of X^TX
Works well when n is large | Slow if n is very large

Q:<br>
Suppose you have the training in the table below:
age (x_1) | height in cm (x_2)| weight in kg (y)
--- | ---| ---
4	|89 |	16
9	|124 |	28
5	|103 |	20

You would like to predict a child's weight as a function of his age and height with the model
weight=θ0+θ1age+θ2height
What are X and y?

A:
> ![](https://latex.codecogs.com/png.latex?%5Cinline%20%5Cbg_white%20X%3D%5Cbegin%7Bbmatrix%7D%201%20%26%204%20%26%2089%20%5C%5C%201%20%26%209%20%26%20124%20%5C%5C%201%20%26%205%20%26%20103%20%5Cend%7Bbmatrix%7D%20y%3D%5Cbegin%7Bbmatrix%7D%2016%5C%5C%2028%5C%5C%2020%5C%5C%20%5Cend%7Bbmatrix%7D)

-----
## Normal Equation Noninvertibility
When implementing the normal equation in octave we want to use the 'pinv' function rather than 'inv.' The 'pinv' function will give you a value of θθ even if X^TX is not invertible.

If X^TX is noninvertible, the common causes might be having :

Redundant features, where two features are very closely related (i.e. they are linearly dependent)
Too many features (e.g. m ≤ n). In this case, delete some features or use "regularization" (to be explained in a later lesson).

Solutions to the above problems include deleting a feature that is linearly dependent with another or deleting one or more features when there are too many features.

-----
## Vectorization
Suppose you have three vector valued variables u, v, wu,v,w:
Your code implements the following:
![](https://latex.codecogs.com/png.latex?%5Cinline%20%5Cbg_white%20%5Cmu%20%3D%5Cbegin%7Bbmatrix%7D%20%5Cmu_1%5C%5C%20%5Cmu_2%5C%5C%20%5Cmu_3%5C%5C%20%5Cend%7Bbmatrix%7D%2C%20%5Cnu%20%3D%5Cbegin%7Bbmatrix%7D%20%5Cnu_1%5C%5C%20%5Cnu_2%5C%5C%20%5Cnu_3%5C%5C%20%5Cend%7Bbmatrix%7D%2C%20%5Comega%20%3D%5Cbegin%7Bbmatrix%7D%20%5Comega_1%5C%5C%20%5Comega_2%5C%5C%20%5Comega_3%5C%5C%20%5Cend%7Bbmatrix%7D%2C)

for j = 1:3,

u(j) = 2 * v(j) + 5 * w(j);

end

How would you vectorize this code?

A:
> - [ ] u = 2 * v' * v * w + 5 * w' * w * v; (where v' denotes the transpose of v)
> - [x] u = 2 * v + 5 * w
> - [ ] u = 5 * v + 2 * w
> - [ ] u = 2 + v + 5 + w