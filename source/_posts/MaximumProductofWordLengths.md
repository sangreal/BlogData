## [LeetCode] Maximum Product of Word Lengths
### Analysis
* We can convert every word into a number which can represent the appearance of every character. Since the length of Int is 32bits. So it is sufficient to use bit to represent them.

### Time Complexity
* MAX(O(n^2), O(n*m))

### Space Comlexity
* O(n)

```cpp
class Solution {
public:
	int convertStr(string word)
	{
		int ret = 0;
		for (char c : word)
		{
			int idx = c-'a';
			ret |= (1 << idx);
		}

		return ret;
	}


    int maxProduct(vector<string>& words) {
    	if (words.size() == 0)
    		return 0;

    	int flag = 0, flag2 = 0;

    	int maxSum = 0;

    	vector<int> nums;
    	for (int i = 0; i < words.size(); i++)
    	{
    		string first = words[i];
    		flag = convertStr(first);
    		nums.push_back(flag);
    	}

    	for (int i = 0; i < nums.size(); i++)
    		for (int j = i+1; j < nums.size(); j++)
    		{
    			if ((nums[i] & nums[j]) == 0)
    			{
    				int len = words[i].length()*words[j].length();
    				maxSum = max(maxSum, len);
    			}
    		}

    	return maxSum;
    }
};
```
