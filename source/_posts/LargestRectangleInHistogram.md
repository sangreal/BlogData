title: "[LeetCode] Largest Rectangle in Histogram"
date: 2016-05-13 18:37:37
tags: [LeetCode, Stack]
---

## Analysis:
> I search from the internet. This is a really skillful solution. In case, I will forget in the future. The key parts are as followed:
> > 1. keep the stack in the incremental order.
> > 2. Compute the width maximum when the stack is empty and height maximum at every step
> > 3. Clear the stack before exit

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def largestRectangleArea(self, heights):
        """
        :type heights: List[int]
        :rtype: int
        """
        if len(heights) == 0:
            return 0
        vec = []
        h = len(heights)
        maxArea = 0
        for i in xrange(len(heights)):
            while len(vec) > 0 and heights[i] <= heights[vec[-1]]:
                idx = vec.pop()
                curArea = i*heights[idx] if len(vec) == 0 else (i-vec[-1]-1)*heights[idx]
                maxArea = max(maxArea, curArea)
            vec.append(i)

        while len(vec) > 0:
            idx = vec.pop()
            curArea = h*heights[idx] if len(vec) == 0 else (h-vec[-1]-1)*heights[idx]
            maxArea = max(maxArea, curArea)

        return maxArea
```
