title: "[LeetCode] Lexicographical Numbers"
date: 2016-08-24 08:37:37
tags: [LeetCode, Depth First Search]
---

## Analysis:
> there are two layers: first determine the base number from [1-9], then DFS through all combinations


## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def dfsHelper(self, base, n, retlist):
        for i in xrange(10):
            curnum = base*10 + i
            if curnum <= n:
                retlist.append(curnum)
                self.dfsHelper(curnum, n, retlist)
            else:
                break

    def lexicalOrder(self, n):
        """
        :type n: int
        :rtype: List[int]
        """
        retlist = []
        for i in xrange(1, 10):
            if i <= n:
                retlist.append(i)
                self.dfsHelper(i, n , retlist)
        return retlist
```
