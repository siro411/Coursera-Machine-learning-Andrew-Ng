# Introduction
> Q1:<br>
Suppose m=4 students have taken some class, and the class had a midterm exam and a final exam. You have collected a dataset of their scores on the two exams, which is as follows:

midterm exam |	(midterm exam)^2 | final exam
---| ---| ---
89 |    7921 |	96
72 |	5184 |  74
94 |	8836 |	87
69 |	4761 |	78

You'd like to use polynomial regression to predict a student's final exam score from their midterm exam score. Concretely, suppose you want to fit a model of the form hθ(x)=θ0+θ1x1+θ2x2.where x_1 is the midterm score and x_2 is (midterm score)^2. Further, you plan to use both feature scaling (dividing by the "max-min", or range, of a feature) and mean normalization.

What is the normalized feature x_2^{(4)}? (Hint: midterm = 89, final = 96 is training example 4.) Please round off your answer to two decimal places and enter in the text box below.

- -0.46

> Q2:<br>
You run gradient descent for 15 iterations
with α=0.3 and compute
J(θ) after each iteration. You find that the
value of J(θ) increases over time. Based on this, which of the following conclusions seems
most plausible?

A:

> - [ ] α=0.3 is an effective choice of learning rate.
> - [ ] Rather than use the current value of α, it'd be more promising to try a larger value of α (say α=1.0).
> - [X] Rather than use the current value of α, it'd be more promising to try a smaller value of α (say α=0.1).



> Q3:<br>
Suppose you have m=14 training examples with n=3 features (excluding the additional all-ones feature for the intercept term, which you should add). The normal equation is θ = (X^TX)^{-1}X^Ty.For the given values of mm and nn, what are the dimensions of θ, X, and y in this equation?

A:
-   X is 14*4,y is 14*1, θ is 4*1


> Q4:<br>
Suppose you have a dataset with m=50 examples and n=2000000 features for each example. You want to use multivariate linear regression to fit the parameters θ to our data. Should you prefer gradient descent or the normal equation?

A:

> - [ ] The normal equation, since gradient descent might be unable to find the optimal θ.
> - [X] Gradient descent, since (X^TX)^{-1} will be very slow to compute in the normal equation.
> - [ ] Gradient descent, since it will always converge to the optimal θ.
> - [ ] The normal equation, since it provides an efficient way to directly find the solution.

> Q5:<br>
Which of the following are reasons for using feature scaling?

A:
> - [ ] It speeds up solving for θ using the normal equation.
> - [x] It speeds up gradient descent by making it require fewer iterations to get to a good solution.
> - [ ] It is necessary to prevent gradient descent from getting stuck in local optima.
> - [ ] It prevents the matrix X^TX (used in the normal equation) from being non-invertable (singular/degenerate).