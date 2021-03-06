title: "[LeetCode] Construct Binary Tree from Preorder and Inorder Traversal"
date: 2016-05-25 18:37:37
tags: [LeetCode, Build Binary Tree]
---

## Analysis:
> find the root node and divide them into two parts, and build recursively into subtrees


## Time Complexity:
> * O(n)

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
	def build(self, prestart, preend, instart,inend):
		if prestart >= preend:
			return None
		root = TreeNode(self.preorder[prestart])
		idx = self.inorder[instart:inend+1].index(root.val)
		root.left = self.build(prestart+1, prestart+idx+1, instart, instart+idx)
		root.right = self.build(prestart+idx+1, preend, instart+idx+1, inend)
		return root


	def buildTree(self, preorder, inorder):
		"""
		:type preorder: List[int]
		:type inorder: List[int]
		:rtype: TreeNode
		"""
		if (len(preorder) == 0):
			return None
		self.preorder = preorder
		self.inorder = inorder
		return self.build(0, len(preorder), 0, len(inorder))

```
