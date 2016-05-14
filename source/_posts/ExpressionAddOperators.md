title: "[LeetCode] Expression Add Operators"
date: 2016-05-09 18:37:37
tags: [LeetCode, Backtracking]
---

## Analysis:
> Since we need to list all the possible routes, therefore backtracking is the right choice.
Then we must ignore all the numbers begined with '0' since it is illegal.
We must store the previous number when computing multiply, `cursum-lastnum+curnum*lastnum` to get the right outcome

## Time Complexity:
> * O(2^n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution(object):
    def addOperators(self, num, target):
        """
        :type num: str
        :type target: int
        :rtype: List[str]
        """
        retlist = []
        def dfs(path, pos, cursum, lastnum):
            leng = len(num)
            if pos == leng and cursum == target:
                retlist.append(path)

            if pos >= leng:
                return

            for i in xrange(pos, leng):
                if i > pos and num[pos] == '0':
                    break

                curnum = int(num[pos:i+1])
                if pos == 0:
                    dfs(path + "" + str(curnum), i+1, curnum, curnum)
                else:
                    dfs(path + "+" + str(curnum), i+1, cursum+curnum, curnum)
                    dfs(path + "-" + str(curnum), i+1, cursum-curnum, -curnum)
                    dfs(path + "*" + str(curnum), i+1, cursum-lastnum+curnum*lastnum, curnum*lastnum)

        dfs("", 0, 0, 0)
        return retlist
```
