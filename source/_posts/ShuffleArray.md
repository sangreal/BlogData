title: "[LeetCode] Shuffle an Array"
date: 2016-08-16 18:37:37
tags: [LeetCode, Math]
---

## Analysis:
> The method to solve this problem, please refer to [Fisher–Yates shuffle](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle#The_modern_algorithm)

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):

    def __init__(self, nums):
        """
        :type nums: List[int]
        :type size: int
        """
        self.orig = nums[:]
        self.curstr = nums[:]

    def reset(self):
        """
        Resets the array to its original configuration and return it.
        :rtype: List[int]
        """
        self.curstr[:] = self.orig
        return self.orig

    def shuffle(self):
        """
        Returns a random shuffling of the array.
        :rtype: List[int]
        """
        lens = len(self.curstr)
        for i in xrange(lens-1, 0, -1):
            j = random.randint(0, i)
            self.curstr[i], self.curstr[j] = self.curstr[j], self.curstr[i]
        return self.curstr
```
