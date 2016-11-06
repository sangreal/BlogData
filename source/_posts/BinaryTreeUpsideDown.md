title: "[LeetCode] Binary Tree Upside Down"
date: 2016-08-23 8:37:37
tags: [LeetCode, Binary Tree]
---

## Analysis:
> * You should use recursion and treat every three nodes as a group
> * Then you can find that the left most node must be the root, then we return it as parent node
> * remember to reset root's left node and right node to NULL

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
	def helper(self, root):
		if root is None:
			return root, None

		if root.left is None and root.right is None:
			return root, root

		parent, newroot = self.helper(root.left)
		parent.right = root
		parent.left = root.right
		root.left, root.right = None, None
		return parent.right, newroot

	def upsideDownBinaryTree(self, root):
		"""
		:type root: TreeNode
		:rtype: TreeNode
		"""
		newroot = None
		__ , newroot = self.helper(root)
		return newroot
```
