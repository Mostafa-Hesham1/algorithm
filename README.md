# 0/1 Knapsack Problem

## Problem Description

The 0/1 Knapsack Problem is a classic optimization problem where given a set of items, each with a weight and a value, determine the number of each item to include in a collection so that the total weight is less than or equal to a given limit, and the total value is as large as possible.

### Example

Consider the following items:
- Item 1: Weight = 1, Value = 10
- Item 2: Weight = 3, Value = 40
- Item 3: Weight = 4, Value = 50
- Item 4: Weight = 5, Value = 70

And a knapsack capacity of 7 units.

### Solution Approach

We use dynamic programming to solve this problem efficiently. The main idea is to build a 2D array `K` where `K[i][w]` represents the maximum value that can be attained with a knapsack capacity of `w` and items up to `i`.

#### Algorithm (Dynamic Programming Approach)

```python
def knapSack(W, wt, val, n): 
    K = [[0 for x in range(W + 1)] for x in range(n + 1)] 
  
    # Build table K[][] in bottom up manner 
    for i in range(n + 1): 
        for w in range(W + 1): 
            if i == 0 or w == 0: 
                K[i][w] = 0
            elif wt[i-1] <= w: 
                K[i][w] = max(val[i-1] + K[i-1][w-wt[i-1]], K[i-1][w]) 
            else: 
                K[i][w] = K[i-1][w] 
    
    return K[n][W]
