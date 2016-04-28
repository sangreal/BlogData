title: "[LeetCode] House Robber III"
date: 2016-03-14 18:37:37
tags: [LeetCode, Depth First Search]
---

## Analysis:
> The depth first search can extract the maximum sum from buttom to the top, that is  *ret = max{root+non-left+non-right, left+right}*
> use the return value to switch the side.

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
	def dfs(self, root):
		if root is None: return 0, 0

		l, nol = self.dfs(root.left)
		r, nor = self.dfs(root.right)

		return max(root.val + nol + nor, l+r), l+r
	def rob(self, root):
		"""
		:type root: TreeNode
		:rtype: int
		"""
		maxret, tmp = self.dfs(root)
		return maxret
```
