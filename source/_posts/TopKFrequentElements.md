title: "[LeetCode] Top K Frequent Elements"
date: 2016-05-03 18:37:37
tags: [LeetCode, Heap, Heap Sort]
---

## Analysis:
> We can construct a mini-heap of size K, please pay attention to the tuple of the heap, the key should be the counter.

## Time Complexity:
> * O(nlogk)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        d = collections.defaultdict(int)
        for t in nums:
            d[t] += 1

        h = []
        for key, v in d.iteritems():
            if len(h) < k:
                heapq.heappush(h, (v, key))
            else:
                hv, hk = h[0]
                if hv < v:
                    heapq.heapreplace(h, (v, key))
        output = []
        while len(h) > 0:
            v, key = heapq.heappop(h)
            output.append(key)
        output.reverse()
        return output
```
