title: "[LeetCode] Counting Bits"
date: 2016-03-19 18:37:37
tags: [LeetCode, Math]
---

## Analysis:
> As the tips in the problem, the list of the incremental sequence can be divided by the pow of 2.
> Then we can repeat the circle of **5 = 4(1) + 1(1)** or **9 = 8(1) + 1(1)** 

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def countBits(self, num):
        """
        :type num: int
        :rtype: List[int]
        """

        retlist = [0 for i in xrange(num+1)]

        pow2, before = 1, 1

        for x in xrange(1, num+1):
            if x == pow2:
                before = 1
                retlist[x] = 1
                pow2 <<= 1
            else:
                retlist[x] = 1 + retlist[before]
                before += 1
        return retlist
```
