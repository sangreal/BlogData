title: "[LeetCode] Reorder List"
date: 2016-05-12 18:37:37
tags: [LeetCode, Linked List]
---

## Analysis:
> 1. find the middle point.
> 2. break from the middle node, set the next node to null (important)
> 3. merge two lists

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(1)


## Code
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def reorderList(self, head):
        """
        :type head: ListNode
        :rtype: void Do not return anything, modify head in-place instead.
        """
        if head is None:
            return

        walker, runner = head, head
        while runner.next and runner.next.next:
            walker = walker.next
            runner = runner.next.next

        mid = walker
        right = mid.next
        if right is None:
            return
        mid.next = None
        prev , cur = None, right
        while cur:
            later= cur.next
            cur.next = prev
            prev = cur
            cur = later

        first, second = head, prev
        i = 0
        while first and second:
            if i%2 ==0:
                later = first.next
                first.next = second
                first = later
            else:
                later = second.next
                second.next = first
                second = later
            i += 1
```
