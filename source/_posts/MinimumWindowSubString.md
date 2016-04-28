title: "[LeetCode] Minimum Window Substring"
date: 2016-03-04 18:37:37
tags: [LeetCode, Two Pointers, String]
---

## Analysis:
> Use left pointer and right pointer to narrow down .
> and skip the word exceed the boundary of the word

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def minWindow(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: str
        """
        strMap = collections.defaultdict()
        for c in t:
            if c not in strMap:
                strMap[c] = 1
            else:
                strMap[c] += 1

        maxleft, maxright = 0, 0
        l, r = 0, 0
        leng, curlen = len(t), 0
        minlen = sys.maxint
        while r < len(s):
            if s[r] in strMap:
                if strMap[s[r]] > 0:
                    curlen += 1
                strMap[s[r]] -= 1
                if curlen >= leng:
                    while l < r:
                        if s[l] in strMap:
                            if strMap[s[l]] == 0:
                                break
                            strMap[s[l]] += 1
                        l += 1
                    if minlen > r-l:
                        minlen = r-l
                        maxleft, maxright = l, r+1
            r += 1

        return s[maxleft:maxright]
```
