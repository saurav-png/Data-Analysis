Vector Autoregression (VAR) is a statistical method used to model the relationship between multiple time series variables. It is an extension of the univariate autoregressive model (AR), which models a single time series variable as a function of its past values. In VAR, we consider multiple time series variables as a system and model each variable as a function of its own past values as well as the past values of other variables in the system.

Let's consider a VAR(p) model with k variables. The VAR(p) model represents each variable as a linear combination of its own lagged values and the lagged values of other variables in the system up to order p. The general equation for a VAR(p) model with k variables can be written as follows:

$$Yt​=c+\sum_{i=1}^{p}​ A_{i}​Y_{t−i}​+ε_{t}$$​

where:

- *Y<sub>t</sub>​* is a k-dimensional vector representing the k time series variables at time t.
- *c* is a constant k-dimensional vector (intercept term).
- *A<sub>i</sub>​* is a *k×k* matrix of coefficients for lag *i*.
- Y<sub>t−i</sub>​ is the lagged k-dimensional vector of variables at time *t−i*.
- *p* is the order of the VAR model, which determines the number of lagged terms used to model each variable.
- *ε<sub>t</sub>* is the k-dimensional vector of error terms at time *t*, assumed to be white noise.
- *t−i* represents the time *i* steps in the past.

To estimate the parameters of the VAR model, we use historical data of the time series variables. We can use techniques like least squares, maximum likelihood, or Bayesian methods to estimate the coefficients.

The VAR model can be used for various purposes, such as forecasting future values of the time series variables, analyzing the dynamic interactions between the variables, and studying the effects of shocks on the system.

Let's illustrate the VAR(1) model (one lag) for two variables (k = 2):

$$Y_{t}​=c+A_{1} ​Y_{t−1}​+ε_{t}$$​
where, $$Y_{t}=\begin{pmatrix} y_{1t} \\ y_{2t}\end{pmatrix}, A_{1}=\begin{pmatrix}a_{11} & a_{12} \\ a_{21} & a_{22}\end{pmatrix}, and c= \begin{pmatrix}c_{1} \\ c_{2}\end{pmatrix}$$
This represents a system of two equations:
$$y_{1t}​=c_{1}​+a_{11}​ \; y_{1, \; t−1}​+a_{12} \; ​y_{2,t−1}​+ε_{1t}$$
$$y_{1t}​=c_{2}​+a_{21}​ \; y_{1, \; t−1}​+a_{22} \; ​y_{2,t−1}​+ε_{2t}$$

Here, we have lagged values of both variables on the right-hand side of each equation.
The estimation process involves estimating the coefficients *c, A<sub>1</sub>​*, and the covariance matrix of the error terms *ε<sub>t</sub>*.
<br>

*Check Aric LaBarr's short explanation on this topic too. His explanations are very straightforward and short. It helps to give you a general idea on the topic (**Yes, his explanations helped me that's why I'm plugging him lol**)*
![](https://www.youtube.com/watch?v=0-FKPJ5KxSo)






**Other Videos for VAR model understanding**

![](https://www.youtube.com/watch?v=XDmwUr01rxM&list=PL92YnqQQ1gbhUVYZnIzIDzYt3TG4j75Do&index=51&ab_channel=CrunchEconometrix)
<br>
![](https://www.youtube.com/watch?v=ITRO9tmFkmE&list=PL92YnqQQ1gbhUVYZnIzIDzYt3TG4j75Do&index=50&ab_channel=CrunchEconometrix)
<br>
![](https://www.youtube.com/watch?v=6Ye0CsfRDJg&ab_channel=ritvikmath)