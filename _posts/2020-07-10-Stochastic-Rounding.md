---
layout: post
title: Stochastic Rounding
---

Stochastic rounding is an unbiased rounding scheme and possesses the desirable property that the expected rounding error is zero.

Examples

- 3.5 has a 50% chance to round to 3, and a 50% chance to round to 4

- 2.4 has a 60% chance to round to 2, and a 40% chance to round to 3

- 1.6 has a 40% chance to round to 1, and a 60% chance to round to 2

- -2.1 has a 90% chance to round to -2, and a 10% chance to round to -3

- -4.7 has a 30% chance to round to -4, and a 70% chance to round to -5

Here is the code snippet, i wrote in python:

///

import numpy as np

def sround(input):
    q = np.absolute(input-np.trunc(input))
    adj = np.random.choice([0,1], size = 1, p = [1-q, q])
    if(input < 0):
        return 1
    ## return our new value
    result = int(np.trunc(input)) + int(adj)
    return result

///

To test this run the below snippet:

a = 0
for i in range(1, 100):
    a+=sround(1.3)
print(a)