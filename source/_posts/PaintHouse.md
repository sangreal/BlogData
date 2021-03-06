title: "[LeetCode] Paint House"
date: 2016-04-28 20:37:37
tags: [LeetCode, Dynamic Programming]
---

## Analysis:
> Typical dynamic programming issue. We define dp[i][j] represents when last i houses painted with minimum cost when i-1th house painted with jth color
The we have:

---
> **dp = [[0 for i in xrange(3)] for j in xrange(len(costs)+1)]**


## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution:
    # @param {int[][]} costs n x 3 cost matrix
    # @return {int} an integer, the minimum cost to paint all houses
    def minCost(self, costs):
        dp = [[0 for i in xrange(3)] for j in xrange(len(costs)+1)]

        for i in xrange(1, len(costs)+1):
            dp[i][0] = min(dp[i-1][1], dp[i-1][2]) + costs[i-1][0]
            dp[i][1] = min(dp[i-1][0], dp[i-1][2]) + costs[i-1][1]
            dp[i][2] = min(dp[i-1][1], dp[i-1][0]) + costs[i-1][2]

        return min(dp[len(costs)][0], dp[len(costs)][1], dp[len(costs)][2])
```
