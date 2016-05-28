title: "[LeetCode] Count Complete Tree Nodes"
date: 2016-05-23 18:37:37
tags: [LeetCode, Binary Search]
---

## Analysis:
> Search the left most and right most node, if the depth of them are the same, then it means that 
this is a complete binary tree (subtree). 
> Otherwise, traverse through the subtrees

## Time Complexity:
> * O(logn^2)

## Space Complexity：
> * O(n)


## Code
```python
# Definition for a binary tree node.
class TreeNode(object):
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None

class Solution(object):
    def countNodes(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if root is None:
            return 0

        lnode, rnode = root, root
        hl, hr = 0, 0
        while lnode:
            lnode = lnode.left
            hl += 1
        while rnode:
            rnode = rnode.right
            hr += 1

        if hl == hr:
            return 2 << hl - 1

        return 1 + self.countNodes(root.left) + self.countNodes(root.right)
```
