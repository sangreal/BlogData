title: "[LeetCode] Third Maximum Number"
date: 2016-10-22 18:37:37
tags: [LeetCode, Array]
---

## Analysis:
> simple question, should pay attention to the constraints to make sure, the same numbers will
not fall to the next level


## Time Complexity:
> * O(n)

## Space Complexity：
> * O(1)


## Code
```python
class Solution(object):
    def thirdMax(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        firstmax, secondmax, thirdmax = -sys.maxint, -sys.maxint, -sys.maxint

        for n in nums:
            if n > firstmax:
                thirdmax = secondmax
                secondmax = firstmax
                firstmax = n
            elif n > secondmax and n < firstmax:
                thirdmax = secondmax
                secondmax = n
            elif n > thirdmax and n < secondmax:
                thirdmax = n

        return thirdmax if thirdmax != -sys.maxint else firstmax
```
