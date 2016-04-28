title: "[LeetCode] Integer Break"
date: 2016-04-20 18:37:37
tags: [LeetCode, Dynamic Programming]
---

## Analysis:
> define a array dp to depict the maximum product of n, then we have
> dp[i+j] = max(max(dp[i], i)*max(dp[j], j), dp[i+j])

## Time Complexity:
> * O(n^2)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def integerBreak(self, n):
    """
    :type n: int
    :rtype: int
    """
    dp = [1] * (n+1)

    for i in xrange(1, n+1):
        for j in xrange(1, i+1):
            if i+j <= n:
	    dp[i+j] = max(max(dp[i], i)*max(dp[j], j), dp[i+j])

    return dp[n]
```
