title: "[LeetCode] Count of Smaller Numbers After Self"
date: 2016-06-06 18:37:37
tags: [LeetCode, Binary Search Tree]
---

## Analysis:
> Use custom TreeNode with `leftcnt` and `cnt` attributes. `leftcnt` depict the numbers smaller than the current node. `cnt` represent the nodes has the same value before current node

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class TreeNode(object):
	def __init__(self, val):
		self.left = None
		self.right = None
		self.leftcnt = 0
		self.cnt = 1
		self.val = val

class BinaryTree(object):
	def __init__(self):
		self.root = None

	def insert(self, val):
		if self.root is None:
			self.root = TreeNode(val)
			return 0
		root = self.root
		cnt = 0

		while root:
			if val < root.val:
				root.leftcnt += 1
				if root.left is None:
					root.left = TreeNode(val)
					break
				root = root.left
			elif val > root.val:
				cnt += root.leftcnt + root.cnt
				if root.right is None:
					root.right = TreeNode(val)
					break
				root = root.right
			else:
				cnt += root.leftcnt
				root.cnt += 1
				break
		return cnt


class Solution(object):
	def countSmaller(self, nums):
		"""
		:type nums: List[int]
		:rtype: List[int]
		"""
		retlist = [0] * len(nums)
		tree = BinaryTree()
		for i in xrange(len(nums)-1, -1, -1):
			retlist[i] = tree.insert(nums[i])
		return retlist
```
