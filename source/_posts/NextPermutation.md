title: "[LeetCode] Next Permutation"
date: 2016-08-21 18:37:37
tags: [LeetCode, array]
---

## Analysis:
> 1. find `j` in array in reverse order that nums[j]<nums[j+1]
> 2. find the first element that nums[i]>nums[j]
> 3. swap the elements nums[i], nums[j]
> 4. reverse nums[j+1:]

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(1)


## Code
```python
class Solution(object):
    def nextPermutation(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        lens = len(nums)
        j = lens-2
        while j >= 0 and nums[j] >= nums[j+1]:
            j -= 1

        if j < 0:
            nums.reverse()
            return

        i = lens-1
        while i > j and nums[i] <= nums[j]:
            i -= 1
        
        nums[i], nums[j] = nums[j], nums[i]
        nums[j+1:] = reversed(nums[j+1:])
```
