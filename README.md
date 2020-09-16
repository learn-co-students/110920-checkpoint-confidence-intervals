## Statistical Distributions


```python
# run this cell without changes
import numpy as np
from scipy import stats
```

### 1. Normal Distributions

Say we have check totals for all checks ever written at a TexMex restaurant. 

The distribution for this population of check totals happens to be normally distributed with a **population mean** of 20 dollars and **population standard deviation** of 3 dollars

#### 1a) Compute the z-score for a 26 dollar check. 

Complete the code in the function below and use it to calculate the answer, and store the answer in `ans1`


```python
def z_score(X, mu, sigma):
    """
    Given sample value X, population mean mu, and population
    standard deviation sigma, calculate the z-score
    """
    ### BEGIN SOLUTION
    return (X - mu)/sigma

from test_scripts.test_class import Test
test = Test()

ans1 = z_score(26, 20, 3)
test.save(ans1, "ans1")
### END SOLUTION

# ans1 = None
# ^ un-comment and replace None with appropriate code
```


```python
# PUT ALL WORK FOR THE ABOVE QUESTION ABOVE THIS CELL
# THIS UNALTERABLE CELL CONTAINS HIDDEN TESTS

# z_score should return a floating point number
assert type(z_score(200, 150, 75)) == float

### BEGIN HIDDEN TESTS

# Testing the functionality of the z_score function
assert z_score(200, 150, 75) == (200-150)/75

### END HIDDEN TESTS
```


```python
# PUT ALL WORK FOR THE ABOVE QUESTION ABOVE THIS CELL
# THIS UNALTERABLE CELL CONTAINS HIDDEN TESTS

# Checking that the variable ans1 has been declared
print('My check has a z-score of {}.'.format(ans1))

### BEGIN HIDDEN TESTS

from test_scripts.test_class import Test
test = Test()

test.run_test(ans1, "ans1")

### END HIDDEN TESTS
```

    My check has a z-score of 2.0.


#### 1b) Approximately what percentage of all checks are less than 26 dollars? Explain how you came to your answer.

You can answer this using the empirical rule or this [z-table](https://www.math.arizona.edu/~rsims/ma464/standardnormaltable.pdf).

According to the empirical rule, 95% of check amounts will be within 
about two standard deviations from the mean. A 26 dollar check amount is 
just at the top end of this region. Adding in the 2.5% of amounts below 
this region, we get 97.5%

Looking up 2.00 in the z-table, we find the answer is 97.7%

### 2. Confidence Intervals

One night, a waiter gets 15 checks with a **sample mean** of 19 dollars and **sample standard deviation** of 3 dollars

#### 2a) Calculate the 95% confidence interval around the mean for this waiter's checks

Complete the code in the function below and use it to calculate the answer, and store the answer in `ans2`


```python
def confidence_interval(x_bar, Z, s, n):
    """
    Given sample mean x_bar, Z-value Z, sample standard
    deviation s, and sample count n, calculate the
    confidence interval around the sample mean
    
    This function should return a tuple containing two
    numbers
    """
    ### BEGIN SOLUTION
    sterr = s/(n**0.5)
    return (x_bar - Z*sterr, x_bar + Z*sterr)


from test_scripts.test_class import Test
test = Test()

ans2 = confidence_interval(19, 1.96, 3, 15)

test.save(ans2, "ans2")

### END SOLUTION

# ans2 = None
# ^ un-comment and replace None with appropriate code
```


```python
# PUT ALL WORK FOR THE ABOVE QUESTION ABOVE THIS CELL
# THIS UNALTERABLE CELL CONTAINS HIDDEN TESTS

# confidence_interval should return a tuple
assert type(confidence_interval(70, 1.96, 5, 50)) == tuple

### BEGIN HIDDEN TESTS

assert confidence_interval(70, 1.96, 5, 50) == (70 - 1.96*(5/(50**0.5)), 70 + 1.96*(5/(50**0.5)))

### END HIDDEN TESTS
```


```python
# PUT ALL WORK FOR THE ABOVE QUESTION ABOVE THIS CELL
# THIS UNALTERABLE CELL CONTAINS HIDDEN TESTS

# Checking that the variable ans2 has been declared
print('The 95% confidence interval is ', ans2)

### BEGIN HIDDEN TESTS

from test_scripts.test_class import Test
test = Test()

test.run_test(ans2, "ans2")

### END HIDDEN TESTS
```

    The 95% confidence interval is  (17.48179052828669, 20.51820947171331)


#### 2b) Interpret the result of this confidence interval calculation

A 95% confidence interval means that, if confidence intervals were generated over and 
over again, using the same method, 95% of the confidence intervals generated will contain 
the true population mean. 

In this case of looking at a single confidence interval, that means we cannot reject
the values between 17.5 and 20.5 for estimates of the mean of checks as a whole with 
an alpha of .05

INCORRECT: a .05 alpha confidence interval contains 95% of all values that samples can have.

INCORRECT: a .05 alpha confidence interval contains 95% of all values in the population.

INCORRECT: there is a 95% chance that the values of the checks the waiter got that 
night are between 17.5 and 20.5
