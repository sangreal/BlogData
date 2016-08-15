title: "[LeetCode] Combination Sum IV"
date: 2016-07-26 18:37:37
tags: [LeetCode, Dynamic Programming]
---

## Analysis:
> define a array dp[i] to depict the possible combination of `i`, then we have
> if `i+j <= target` then `dp[i+j] += dp[i]`

## Time Complexity:
> * O(n^2)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def combinationSum4(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        dp = [0] * (target+1)
        dp[0] = 1
        for x in xrange(target+1):
            for y in nums:
                if x + y <= target:
                    dp[x+y] += dp[x]
        return dp[target]

```
