title: "[LeetCode] Best Time to Buy and Sell Stock with Cooldown"
date: 2016-06-17 18:37:37
tags: [LeetCode, Dynamic Programming]
---

## Analysis:
> we use `sells` to depict whether the maximum profit when selling stock at price[i]
> and `buys` to depict the maximum profit when buying at prices[i]
> so we can get 
`sells[i] = max(sells[i-1], buys[i-1]+prices[i])`
`buys[i] = max(buys[i-1], sells[i-2]-prices[i])`

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
	def maxProfit(self, prices):
		"""
		:type prices: List[int]
		:rtype: int
		"""
		if len(prices) < 2:
			return 0

		sells = [0] * len(prices)
		buys = [0] * len(prices)

		sells[0], sells[1] = 0, max(0, prices[1]-prices[0])
		buys[0], buys[1] = -prices[0], max(-prices[0], -prices[1])

		for i in xrange(2, len(prices)):
			sells[i] = max(sells[i-1], buys[i-1]+prices[i])
			buys[i] = max(buys[i-1], sells[i-2]-prices[i])

		return sells[-1]


```
