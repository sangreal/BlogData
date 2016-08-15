title: "[LeetCode] Insert Delete GetRandom O(1)"
date: 2016-08-14 18:37:37
tags: [LeetCode, System Design]
---

## Analysis:
> define a dictionary to store the elements and a vector to store the index of them.
> the key of removal is to move the tail element to the slot of removal element and update the tail element index.

## Time Complexity:
> * O(1)

## Space Complexity：
> * O(n)


## Code
```python
class RandomizedSet(object):

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.storemap = collections.defaultdict(int)
        self.vec = []
        self.lens = 0

    def insert(self, val):
        """
        Inserts a value to the set. Returns true if the set did not already contain the specified element.
        :type val: int
        :rtype: bool
        """
        if val not in self.storemap:
            self.storemap[val] = self.lens
            self.vec.append(val)
            self.lens += 1
            return True
        else:
            return False
        

    def remove(self, val):
        """
        Removes a value from the set. Returns true if the set contained the specified element.
        :type val: int
        :rtype: bool
        """
        if val in self.storemap:
            idx = self.storemap[val]
            tail = self.vec.pop()
            if idx < len(self.vec):
                self.vec[idx] = tail
                self.storemap[tail] = idx
            del self.storemap[val]
            self.lens -= 1
            return True
        else:
            return False
        

    def getRandom(self):
        """
        Get a random element from the set.
        :rtype: int
        """
        return random.choice(self.vec)
        
```
