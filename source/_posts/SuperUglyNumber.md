title: "[LeetCode] Super Ugly Number"
date: 2016-04-12 18:37:37
tags: [LeetCode, Mafia fight]
---

## Analysis:
> Using the mafia fight method, find the smallest prime and multiply with the additional list to store the ugly numbers then adding the relevant indexes of them. Finally pop the last element.


## Time Complexity:
> * O(m*n)

## Space Complexity：
> * O(n)


## Code
```python
class Solution:
    # @param {int} n a positive integer
    # @param {int[]} primes the given prime list
    # @return {int} the nth super ugly number
    def nthSuperUglyNumber(self, n, primes):
        if len(primes) == 0:
            return 1

        idxlist = [0 for i in xrange(len(primes))]
        q = [1]

        minint = sys.maxint
        for i in xrange(1, n):
            minint = sys.maxint
            for j in xrange(len(primes)):
                minint = min(minint, primes[j]*q[idxlist[j]])
            q.append(minint)
            for j in xrange(len(primes)):
                if minint == primes[j]*q[idxlist[j]]:
                    idxlist[j] += 1

        return q[-1]
```
