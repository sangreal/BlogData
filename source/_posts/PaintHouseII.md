title: "[LeetCode] Paint House II"
date: 2016-04-28 20:37:37
tags: [LeetCode, Dynamic Programming]
---

## Analysis:
> Complicated than the `Paint House` since the number of color is not certain. Therefore, we have to store the minIdx, minVal and second small value in case that the minimum value is the same in the last level


## Time Complexity:
> * O(nk)

## Space Complexity：
> * O(nk)


## Code
```python
class Solution:
    # @param {int[][]} costs n x k cost matrix
    # @return {int} an integer, the minimum cost to paint all houses
    def minCostII(self, costs):
        if len(costs) == 0 or len(costs[0]) == 0:
            return 0

        siz = len(costs)
        k = len(costs[0])

        dp = [[0 for i in xrange(k)] for j in xrange(len(costs)+1)]

        for i in xrange(1, len(costs)+1):
            minval, secminval, minIdx = dp[i-1][0], dp[i-1][0], 0
            for t in xrange(k):
                if dp[i-1][t] < minval:
                    secminval = minval
                    minval = dp[i-1][t]
                    minIdx = t
                elif dp[i-1][t] < secminval:
                    secminval = dp[i-1][t]
            for j in xrange(k):
                if minIdx == j:
                    dp[i][j] = secminval + costs[i-1][j]
                else:
                    dp[i][j] = minval + costs[i-1][j]

        retMin = dp[siz][0]
        for t in xrange(1, k):
            retMin = min(retMin, dp[siz][t])

        return retMin
```
