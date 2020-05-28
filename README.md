## Statistical Distributions


```python
# import the necessary libraries
import numpy as np
from scipy import stats
```


```python
# __SOLUTION__ 
# import the necessary libraries
import numpy as np
from scipy import stats
```

### 1. Normal Distributions

Say we have check totals for all checks ever written at a TexMex restaurant. 

The distribution for this population of check totals happens to be normally distributed with a population mean of 20 dollars and population standard deviation of 3 dollars

#### 1a) Compute the z-score for a 26 dollar check. 

Complete the code in the function below and use it to calculate the answer


```python
def z_score(check_amt):
    """
    check_amt = the amount for which we want to compute the z-score
    """
    
    score = #your code here
    return score

#Use the function here to calculate your score
```


```python
# __SOLUTION__ 
def z_score(check_amt):
    
    """ Using the formula (X - mu)/std """
    
    return (check_amt - 20)/3

print('My check has a z-score of {}.'.format(z_score(26)))
```

    My check has a z-score of 2.0.


#### 1b) Approximately what percentage of all checks are less than 26 dollars? Explain how you came to your answer.

You can answer this using the empirical rule or this [z-table](https://www.math.arizona.edu/~rsims/ma464/standardnormaltable.pdf).


```python
"""
Written answer here
"""
```


```python
# __SOLUTION__
"""
According to the empirical rule, 95% of check amounts will be within 
about two standard deviations from the mean. A 26 dollar check amount is 
just at the top end of this region. Adding in the 2.5% of amounts below 
this region, we get 97.5%

Looking up 2.00 in the z-table, we find the answer is 97.7%
"""
```

    
    According to the empirical rule, 95% of check amounts will be within 
    about two standard deviations from the mean. A 26 dollar check amount is 
    just at the top end of this region. Adding in the 2.5% of amounts below 
    this region, we get 97.5%
    
    Looking up 2.00 in the z-table, we find the answer is 97.7%
    


### 2. Confidence Intervals

One night, a waiter gets 15 checks with a mean of 19 dollars and standard deviation of 3 dollars

#### 2a) Calculate the 95% confidence interval around the mean for this waitor's checks


```python
#Your code here
```


```python
#__SOLUTION__


mu = 19
std = 3
n = 15

sterr = std/(n**0.5)
conf = (mu - 1.96*sterr, mu + 1.96*sterr)
print('The 95% confidence interval is ', conf)
```

    The 95% confidence interval is  (17.48179052828669, 20.51820947171331)


#### 2b) Interpret the result


```python
"""

Your written answer here

"""
```


```python
# __SOLUTION__
"""
A 95% confidence interval means that there is a 95% chance for the
interval to contain the true population mean. In this case, that means 
there is a 95% chance that the true population mean is between 17.5 and 20.5

INCORRECT: a confidence interval contains 95% of all values that samples can have.

INCORRECT: a confidence interval contains 95% of all values in the population.

INCORRECT: there is a 95% chance that the values of the checks the waiter got that night are between 17.5 and 20.5
"""
```
