title: "[LeetCode] H-Index"
date: 2016-01-14 22:41:28
tags: LeetCode
---

## Analysis:
> Sort it first, then you can find the index when citation[idx] >= idx+1

## Time Complexity:
> * O(nlogn)

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
        citations.sort(reverse = True)
        idx = 0

        for x in xrange(len(citations)):
            if citations[x] >= x+1:
                idx += 1
        return idx
```
