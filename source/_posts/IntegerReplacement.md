title: "[LeetCode] Integer Replacement"
date: 2016-09-15 18:37:37
tags: [LeetCode, Math]
---

## Analysis:
> treat it as a tree, find the path to the leaf with minimum hops
> 

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def integerReplacement(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n == 1:
            return 0

        if n%2 == 0:
            return self.integerReplacement(n/2)+1
        else:
            return min(self.integerReplacement(n-1), self.integerReplacement(n+1)) + 1
```
