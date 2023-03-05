# Random Number Distributions for Investment Analysis
This project explores the distributions and their applications for investment analysis.  We can use monte carlo simulations to generate random variables from different distributions and use the results to calculate the probablities that an event will occur. This is often a practical approach to modelling complex investment scenarios.


## Visualizing Distribuitons & Calculating Probabilities
+Three helper functions were built using plotly to visualize distributions
+ probablity density plot (pdf)
+ cumulative probability density plot (cdf)
+ calculate_probabilities - this function can be used to count the occurances of specific events in the simulated distribtion. This allows us to calculate specific probabilities

## Discrete Uniform Distributions
In this distribution, a value can take on a finite or infinite number of countable values (whole numbers)
+ X(x1, x2, ....xn), where X = discreate random variable, xn=value of variable
+ A coin toss of fair or bias die is a common example where this distribtion is used.  In investments, we could model the number of shares traded in a day 
#### Example
  + Roll a fair and bias die, and calculate the associated probabilities of rolling exactly 3, or a die less than 3
  + Probability of rolling a 3 (fair) = 16.60%
  + Probability of rolling a 3 (bias) = 51.54%
  + Probability of rolling less than 3 (fair) = 33.90%
  + Probability of rolling less than 3 (bias) = 9.79%

![image](https://user-images.githubusercontent.com/1649676/222987287-241dcedd-9f5d-432c-aeaf-9846d22efc01.png)


## Binomial Distributions
This distribion is used to model true/false events, ie somethign occurs or it doesn't. This distribiont is also known as bernoulli random variables.  
+ n=number of trials
+ probabiliy of success = p
+ probability of failure = (1-p)
+ N=number of successes

`p(N) = ( n chose N ) p^N ( 1 − p)^ n−N`  
`p(N) = n! / (n-N)!N! * p^N(1-p)^n-N `

#### Example: The Expected Number of Defaults in a Bond Portfolio
Estimate the number of bond issues expected to default over the next year in a high-yield bond portfolio
with 25 US issuers. The estimated annual default rate for B2/B rated bonds is 10.7%.
+ Probability of all bonds defaulting = 0.00%
+ Probability of no bonds defaulting = 5.83
+ Probability of 5 or more bonds defaulting = 11.63%

![image](https://user-images.githubusercontent.com/1649676/222987933-bd516d06-3b34-4f8b-95c3-c30dc54eff43.png)

## Normal Distribution
Often used to model an assets returns (but not an assets price=> see lognormal distrtibution instead)
+ symmetrical and bell shaped
+ require two parameters: mu (mean), and sigma (standard deviation)
+ skewness=0 (symmetric)
+ mean==median=mode
+ standard normal (unit) distribution
    + mu = 0
    + sigma = 1
    + 68% of all observations fall within mu +/- sigma
    + 95% of all observations fall within mu +/- 2sigma
    + 99% of all observations fall within mu +/- 3sigma

### Univariate Distribution
+ Model portfolio assets individually as a single random variable
+ nearly all the probablity of an assets returns are contained within 2 standard deviations of the mean
+ to model independent securities requires the following:
    + mean return of the security returns
    + standard deviation of the security returns

### Multivariate Distribution
+ Model portfolio assets as a group of related random variables in a portfolio
+ To model a portfolio of non-independent securities requires the following
    + mean returns of the individual securities
    + standard deviation of individual security returns
    + pairwise correlations between individual security returns
    + For a full example of a multivariate distribution using a monte carlo simultion have a look at the [monte-carlo-for-investment](https://github.com/kconstable/monte-carlo-for-investments) github project

#### Single Assets Returns
We can model individual asset returns, assuming they are independent from each other. We generate normal random varibles for each assets mean & standard deviation, then count the number of occurences for each event to determine the probabilities
+ Probbility that a1 <= 1 sigma below mu = 15.65%
+ Probabilty that a1 returns are between -1 sigma and +1 sigma = 68.26%
+ Probability that a1 returns are below 2 standard deviations below mu = 2.26%
+ Probability that a2 returns are less than 2 standard deviations below mu = 15.51%


![image](https://user-images.githubusercontent.com/1649676/222988165-36745104-7dab-4c8c-aff0-940fd7feb6b0.png)




