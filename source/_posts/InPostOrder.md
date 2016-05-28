title: "[LeetCode] Construct Binary Tree from Inorder and Postorder Traversal"
date: 2016-05-28 18:37:37
tags: [LeetCode, Build Binary Tree]
---

## Analysis:
> find the root node and divide them into two parts, and build recursively into subtrees
> the difference is that root is always the last one

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):

    def build(self, instart, inend, poststart, postend):
        if poststart >= postend:
            return None

        root = TreeNode(self.postorder[postend-1])
        idx = self.inorder[instart:inend+1].index(root.val)
        root.left = self.build(instart, instart+idx, poststart, poststart+idx)
        root.right = self.build(instart+idx+1, inend, poststart+idx, postend-1)
        return root

    def buildTree(self, inorder, postorder):
        """
        :type inorder: List[int]
        :type postorder: List[int]
        :rtype: TreeNode
        """
        if len(inorder) == 0:
            return None
        self.inorder = inorder
        self.postorder = postorder
        return self.build(0, len(inorder), 0, len(postorder))

```
