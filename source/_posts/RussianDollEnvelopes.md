title: "[LeetCode] Russian Doll Envelopes"
date: 2016-06-10 18:37:37
tags: [LeetCode, Dynamic Programming]
---

## Analysis:
> Another form of Longest Increasing Sequence.

## Time Complexity:
> * O(nlogn)

## Space Complexity：
> * O(n)


## Code
```cpp
class Solution {
public:
    int maxEnvelopes(vector<pair<int, int>>& envelopes) {
    	auto cmp = [](pair<int, int> a, pair<int, int> b) {return a.first < b.first;};

    	std::sort(envelopes.begin(), envelopes.end(), cmp);

    	int maxnum = 0;
    	vector<int> dp (envelopes.size(), 1);
    	for (int i = 1; i < envelopes.size();i++) {
    		for (int j = 0; j < i; j++) {
				pair<int, int> prev = envelopes[j];
				pair<int, int> cur = envelopes[i];

				if (prev.first < cur.first && prev.second < cur.second) {
					dp[i] = max(dp[i], 1+dp[j]);
				}
    		}
    	}

    	for (int p : dp) {
    		maxnum = max(maxnum, p);
    	}
    	return maxnum;

    }
};
```
