
## Statistical Distributions [Suggested time: 25 minutes]


```
# import the necessary libraries
import numpy as np
from scipy import stats
```

### a. Normal Distributions

Say we have check totals for all checks ever written at a TexMex restaurant. 

The distribution for this population of check totals happens to be normally distributed with a population mean of $\mu = 20$ and population standard deviation of $\sigma = 2$. 

2.a.1) Write a function to compute the z-scores for single checks of amount `check_amt`.


```
def z_score(check_amt):
    
    """ Using the formula (X - mu)/std """
    
    return (check_amt - 20)/2
```

2.a.2) I go to the TexMex restaurant and get a check for 24 dollars. 

Use your function to compute your check's z-score, and interpret the result using the empirical rule. 


```
print("My check has a z-score of {}.".format(z_score(24)))
```


```
# The z-score of your check tells you how many standard deviations your check amount is away from the mean
# check amount. In this case, your check is two standard deviations away from the mean.

# According to the empirical rule, 95% of expected check amounts will be within two standard deviations from the mean.
# Your check amount is just within this region.
```

2.a.3) Using $\alpha = 0.05$, is my 25 dollar check significantly **greater** than the mean? How do you know this?  

Hint: Here's a link to a [z-table](https://www.math.arizona.edu/~rsims/ma464/standardnormaltable.pdf). 


```
print("My check has a z-score of {}.".format(z_score(24)))
print("The critical threshold z is {}.".format(round(stats.norm.ppf(0.95),2)))
```


```
# For alpha = 0.05, the critical threshold z for an upper-tailed z-test is 1.64 (this can be found using the linked z-table or scipy.stats.)
# We obtain a z-score of 2.5, which is greater than the critical threshold of 1.64. 
# Thus, my 25 dollar check is significantly greater than the mean at alpha = 0.05. 
```

### b. Confidence Intervals and the Central Limit Theorem

2.b.1) Determine the 95% confidence interval around the mean check total for this population. Interpret your result. 


```
# 95% confidence interval has z-score of 1.96 (read where p = 0.975)
mean = 20
std = 2
conf = (mean - 1.96*std, mean + 1.96*std)
print("The 95% confidence interval is ", conf)
```


```
"""
A 95% confidence interval means that there is a 95% chance for the interval to contain the true population mean.

A confidence interval is an interval containing the true population mean with a certain probability. 
i.e. For a 95% confidence interval, there is a 95% chance the interval contains the true population mean.

Frequentist interpretation of the confidence interval:  
Were this procedure to be repeated on 100 samples, approximately 95 of the calculated confidence intervals 
(which would be different for each sample) would be expected to contain the true population mean.

INCORRECT: a confidence interval contains 95% of all values.
"""
```

2.b.2) Imagine that we didn't know how the population of check totals was distributed. How would **sampling** and the **Central Limit Theorem** allow us to **make inferences on the population mean**, i.e. estimate $\mu, \sigma$ of the population mean?


```
"""
Solution: The Central Limit Theorem says that we can take repeated samples of the population, 
and estimate population parameters by finding the average mean and standard deviation of the samples. 
Sample means will also tend to a normal distribution.
"""
```
