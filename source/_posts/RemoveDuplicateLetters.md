title: "[LeetCode] Remove Duplicate Letters"
date: 2016-06-19 18:37:37
tags: [LeetCode, Stack, Greedy]
---

## Analysis:
> using a stack to keep the always increasing order of the results.
using a set to track the elements containing current answer result.
> The key point is to ensure the order by comparing the current number with the tail number in the stack only if the counter of it is large than 1


## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def removeDuplicateLetters(self, s):
        """
        :type s: str
        :rtype: str
        """
        store = []
        resultSet = set()

        count = collections.Counter(s)

        for n in s:
            count[n] -= 1
            if n in resultSet:
                continue
            while len(store) > 0 and store[-1] > n and count[store[-1]] > 0:
                resultSet.remove(store.pop())
            resultSet.add(n)
            store.append(n)

        return ''.join(store)
```
