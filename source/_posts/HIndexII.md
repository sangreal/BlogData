title: "[LeetCode] H-Index II"
date: 2016-01-15 22:51:23
tags: LeetCode
---

## Analysis:
> Since the array has already been sorted, we can use binary search to find the pivot point

## Time Complexity:
> * O(logn)

## Space Complexity：
> * O(1)


## Code
```python
class Solution(object):
    def hIndex(self, citations):
        """
        :type citations: List[int]
        :rtype: int
        """
        l, r = 0, len(citations)-1
        length = len(citations)-1
        while l <= r:
            mid = l + (r-l)/2
            idx = length-mid
            if citations[mid] >= idx+1:
                r = mid-1
            else:
                l = mid+1
        return length-l+1
```
