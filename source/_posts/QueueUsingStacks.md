title: "[LeetCode] Implement Queue using Stacks"
date: 2016-03-07 18:37:37
tags: [LeetCode, Data Structure Design]
---

## Analysis:
> There should be two stacks, one for push and one for pop. 
> > Rule 1: always push items into the store stack
> > Rule 2: pop from the pop stack, and if not, we should pop from store stack and push them into pop stack 
> Average time is O(1), since if one-time pop takes O(k), then the next k-time actions only take O(1). 

## Time Complexity:
> * O(1)

## Space Complexity：
> * O(n)


## Code
```python
import collections

class Queue(object):
    def __init__(self):
        """
        initialize your data structure here.
        """
        self.exStack = collections.deque()
        self.storeStack = collections.deque()

    def push(self, x):
        """
        :type x: int
        :rtype: nothing
        """
        self.storeStack.append(x)

    def pop(self):
        """
        :rtype: nothing
        """
        if len(self.exStack) == 0:
            for x in xrange(len(self.storeStack)):
                self.exStack.append(self.storeStack.pop())
        if len(self.exStack) > 0:
            self.exStack.pop()


    def peek(self):
        """
        :rtype: int
        """
        if len(self.exStack) == 0:
            for x in xrange(len(self.storeStack)):
                self.exStack.append(self.storeStack.pop())
        if len(self.exStack) > 0:
            return self.exStack[-1]
        else:
            return 0

    def empty(self):
        """
        :rtype: bool
        """
        return len(self.exStack) == 0 and len(self.storeStack) == 0
```
