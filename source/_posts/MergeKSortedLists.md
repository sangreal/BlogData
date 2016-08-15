title: "[LeetCode] Merge k Sorted Lists"
date: 2016-06-25 18:37:37
tags: [LeetCode, Heap]
---

## Analysis:
> define a heap to store the first node of lists, then pop the top node and push back the next node into heap, until the heap is empty

## Time Complexity:
> * O(nlogn)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def mergeKLists(self, lists):
        """
        :type lists: List[ListNode]
        :rtype: ListNode
        """
        if len(lists) == 0:
            return []
        heaplist = []
        for node in lists:
            if node:
                heaplist.append((node.val, node))

        heapq.heapify(heaplist)
        head = ListNode(-1)
        dummy = head
        while len(heaplist) > 0:
            topval, topnode = heapq.heappop(heaplist)
            dummy.next = topnode
            dummy = dummy.next

            if topnode.next:
                heapq.heappush(heaplist, (topnode.next.val, topnode.next))
        return head.next
```
