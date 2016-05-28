title: "[LeetCode] Candy"
date: 2016-05-17 18:37:37
tags: [LeetCode, Greedy]
---

## Analysis:
> two times traversal, first traversal ensure `dp[i] > dp[i-1]` if `rating[i] > rating[i-1]`
> and the reverse traversal, to ensure `dp[i] > dp[i+1]` if `rating[i] > rating[i+1]`

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
	def candy(self, ratings):
		"""
		:type ratings: List[int]
		:rtype: int
		"""
		dp = [1 for i in xrange(len(ratings))]
		for i in xrange(1, len(ratings)):
			if ratings[i] > ratings[i-1]:
				dp[i] = dp[i-1] + 1

		for j in xrange(len(ratings)-2, -1, -1):
			if ratings[j] > ratings[j+1] and dp[j] <= dp[j+1]:
				dp[j] += dp[j+1]-dp[j]+1
		retsum = 0
		for n in dp:
			retsum += n
		return retsum
```
