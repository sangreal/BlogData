title: "[LeetCode] Recover Binary Search Tree"
date: 2016-03-09 18:37:37
tags: [LeetCode, Tree]
---

## Analysis:
> Use in-order traversal to find the disorder node pairs.
> > * If there is one pair: that means the swap nodes are adjacent.
> > * If ther are two pair: they are not next to each other.

> Finally swap them by value. This is not the optimal solution. BTW

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def recoverTree(self, root):
        """
        :type root: TreeNode
        :rtype: void Do not return anything, modify root in-place instead.
        """
        if root is None: return

        vec = []
        prev = None
        node1, node2 = None,None
        p = root

        count = 0
        while len(vec) > 0 or p is not None:
            if p is not None:
                vec.append(p)
                p = p.left
            else:
                p = vec.pop()
                if prev is None:
                    prev = p
                else:
                    if prev.val > p.val:
                        count += 1
                        if node1 is None:
                            node1 = prev
                            node2 = p
                        elif count > 1:
                            node2 = p
                prev = p
                p = p.right

        node1.val, node2.val = node2.val, node1.val
```
