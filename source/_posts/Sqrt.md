title: "[LeetCode] Sqrt(x)"
date: 2016-04-26 18:37:37
tags: [LeetCode, Binary Search]
---

## Analysis:
> Use binary search to solve it, pay attention to the floor of integer.

## Time Complexity:
> * O(logn)

## Space Complexity：
> * O(1)


## Code
```python
class Solution(object):
  def mySqrt(self, x):
  """
  :type x: int
  :rtype: int
  """

  l, r = 0, x
  while l <= r:
    mid = l + (r-l)/2
    if mid*mid == x or (mid*mid < x and (mid+1)*(mid+1) > x):
      return mid
    elif mid*mid < x:
      l = mid+1
    else:
      r = mid-1

  return -1
```
