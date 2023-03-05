# Random Number Distributions for Investment Analysis
This project explores the distributions and their applications for investment analysis.  We can use monte carlo simulations to generate random variables from different distributions and use the results to calculate the probabilities that an event will occur. This is often a practical approach to modeling complex investment scenarios.


## Visualizing Distributions & Calculating Probabilities
+Three helper functions were built using plotly to visualize distributions
+ probability density plot (pdf)
+ cumulative probability density plot (cdf)
+ calculate_probabilities - this function can be used to count the occurrences of specific events in the simulated distribution. This allows us to calculate specific probabilities

## Discrete Uniform Distributions
In this distribution, a value can take on a finite or infinite number of countable values (whole numbers)
+ X(x1, x2, ....xn), where X = discrete random variable, xn=value of variable
+ A coin toss of the fair or biased die is a common example where this distribution is used.  In investments, we could model the number of shares traded in a day 
#### Example
  + Roll a fair and biased die, and calculate the associated probabilities of rolling exactly 3, or a die less than 3
  + Probability of rolling a 3 (fair) = 16.60%
  + Probability of rolling a 3 (bias) = 51.54%
  + Probability of rolling less than 3 (fair) = 33.90%
  + Probability of rolling less than 3 (bias) = 9.79%

![image](https://user-images.githubusercontent.com/1649676/222987287-241dcedd-9f5d-432c-aeaf-9846d22efc01.png)


## Binomial Distributions
This distribution is used to model true/false events, ie something occurs or it doesn't. This distribution is also known as bernoulli random variables.  
+ n=number of trials
+ probability of success = p
+ probability of failure = (1-p)
+ N=number of successes

`p(N) = ( n chose N ) p^N ( 1 − p)^ n−N`  
`p(N) = n! / (n-N)!N! * p^N(1-p)^n-N `

#### Example: The Expected Number of Defaults in a Bond Portfolio
Estimate the number of bond issues expected to default over the next year in a high-yield bond portfolio
with 25 US issuers. The estimated annual default rate for B2/B-rated bonds is 10.7%.
+ Probability of all bonds defaulting = 0.00%
+ Probability of no bonds defaulting = 5.83
+ Probability of 5 or more bonds defaulting = 11.63%

![image](https://user-images.githubusercontent.com/1649676/222987933-bd516d06-3b34-4f8b-95c3-c30dc54eff43.png)

## Normal Distribution
Often used to model an assets returns (but not an assets price=> see lognormal distribution instead)
+ symmetrical and bell-shaped
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
+ nearly all the probability of an assets returns are contained within 2 standard deviations of the mean
+ to model-independent securities requires the following:
    + mean return of the security returns
    + standard deviation of the security returns

### Multivariate Distribution
+ Model portfolio assets as a group of related random variables in a portfolio
+ To model a portfolio of non-independent securities requires the following
    + mean returns of the individual securities
    + standard deviation of individual security returns
    + pairwise correlations between individual security returns
    + For a full example of a multivariate distribution using a monte carlo simulation have a look at the [monte-carlo-for-investment](https://github.com/kconstable/monte-carlo-for-investments) github project

#### Example 1: Single Assets Returns
We can model individual asset returns, assuming they are independent of each other. We generate normal random variables for each assets mean & standard deviation, then count the number of occurrences for each event to determine the probabilities
+ Probability that a1 <= 1 sigma below mu = 15.65%
+ Probability that a1 returns are between -1 sigma and +1 sigma = 68.26%
+ Probability that a1 returns are below 2 standard deviations below mu = 2.26%
+ Probability that a2 returns are less than 2 standard deviations below mu = 15.51%

![image](https://user-images.githubusercontent.com/1649676/222988165-36745104-7dab-4c8c-aff0-940fd7feb6b0.png)

#### Example 2: Portfolio Shortfall Risk
A Portfolio value is 800,000, and we want to ensure we can withdraw $30,000 without invading the initial capital of the portfolio. Given three different portfolio allocations;
+ What is the return shortfall level?
+ which allocation is the best to preserve the capital above the shortfall level?
+ what is the probability the optimal safety-first portfolio will be less than the shortfall level?

| Allocation         | A  | B  | C  |
|--------------------|----|----|----|
| Expected Return    | 25 | 11 | 14 |
| Standard Deviation | 27 | 8  | 20 |

+ Shortfall Level:3.75%
+ SFRatio (P1):0.79
+ SFRatio (P2

![image](https://user-images.githubusercontent.com/1649676/222988611-3dd6f11d-720c-4411-8246-dd2ebfdc48c4.png)


## Lognormal Distribution
Lognormal distributions are often used to model a securities price, which has a minimum value of zero but no maximum value and skews to the right.  If you want to model a portfolios returns you can use a normal distribution or a student t-distribution
+ params
    + mean of its normal distribution ln(y)
    + standard deviation of its normal distribution ln(y)


## Students T Distribution
+ A family of symmetrical distributions with fatter tails than the normal distribution, similar to asset returns
+ Defined by a single parameter=degrees of freedom (df) (sample-size)
+ The higher the df, the closer the t-distribution is to the normal distribution (the tails get thinner with increasing sample size)

#### Applications in Investments
+ Often used to model asset returns as it can provide a better estimate of downside risk estimates
+ The scipy library in python can be used to generate a t-distribution for a given assets mean, sigma, and degrees of freedom
+ t-statistic
    + test of a single population mean
    + test of differences between two population means
    + mean difference of paired (dependent) populations
    + test of correlation coefficients

![image](https://user-images.githubusercontent.com/1649676/222988806-886d90ba-d655-41d9-89ab-36819d8bf568.png)


## Chi-Square Distribution
+ Asymmetrical family of distributions
+ sum of the squares of k independent standard random variables (will only have positive values)
+ The distribution varies with degrees of freedom
+ The scipy library in python can be used to generate a t-distribution for a given assets mean, sigma and degrees of freedom

**Applications in Investments**
+ chi-square statistic
    + test of variance of a normally distributed population
![image](https://user-images.githubusercontent.com/1649676/222988918-73c99e3a-34f9-427f-900e-629ce601a281.png)


## F-Distribution
+ Asymmetrical family of distributions
+ ratio of chi-squared distributions df(numerator)/df(denominator)
+ only positive values
+ as df increases, the f-distribution approaches the normal distribution
+ The scipy library in python can be used to generate a t-distribution for a given assets mean, and degrees of freedom for the denominator, and numerator

**Applications in Investments**
+ F-statistic
    + test of equality of variances of two normally distributed populations

![image](https://user-images.githubusercontent.com/1649676/222989023-42781cb8-4cf1-49d3-92dd-9394a2536965.png)

