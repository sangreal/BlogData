title: "[LeetCode] Maximum Size Subarray Sum Equals k"
date: 2016-08-18 18:37:37
tags: [LeetCode, Hash Table]
---

## Analysis:
> use a dict to store sum of range sum as key and index as value
> we can check if the remaining in the dict. If so, find the largest gap of them.

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def maxSubArrayLen(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        sumstore = collections.defaultdict(list)
        cursum = 0
        for i in xrange(len(nums)):
            cursum += nums[i]
            sumstore[cursum].append(i)

        retval = 0
        for t in sumstore.keys():
            if t == k:
                retval = max(retval, sumstore[t][-1]+1)
            elif t-k in sumstore:
                retval = max(retval, sumstore[t][-1]-sumstore[t-k][0])
        return retval 
```
