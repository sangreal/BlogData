title: "[LeetCode] Verify Preorder Serialization of a Binary Tree"
date: 2016-02-10 22:10:54
tags: [LeetCode, Tree]
---

### Analysis
* Stack can be used here to store the elements, one '#' for one element and two '#'. And check if there is one '#' remains in the stack, which means this is a valid pre-order

### Time Complexity
* O(n)

### Space Comlexity
* O(n)

### Code
```python
class Solution(object):
    def isValidSerialization(self, preorder):
        """
        :type preorder: str
        :rtype: bool
        """
        store = collections.deque()

        for item in preorder.split(','):
        	store.append(item)
        	while len(store) > 2 and store[-1] == '#' and store[-2] == '#' and store[-3] != '#':
    			store.pop()
    			store.pop()
    			store[-1] = '#'

    	return len(store) == 1 and store[0] == '#'
```
