# 3917. Count Indices With Opposite Parity  

**Difficulty:** Easy  
**Topics:** Array   
**LeetCode:** https://leetcode.com/problems/count-indices-with-opposite-parity/description/ 

---

## Solution 1 - Array

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<int> countOppositeParity(vector<int>& nums) {
        vector<int> ans;
        int n = nums.size();
        vector<int> even(n+1,0),odd(n+1,0);
        for(int i=n-1;i>=0;i--)
        {
            if(nums[i]%2==0)
            {
                even[i] = even[i+1]+1;
                odd[i] = odd[i+1];
            }
            else
            {
                odd[i] = odd[i+1]+1;
                even[i] = even[i+1];
            }
        }
        for(int i=0;i<n;i++)
        {
            if(nums[i]%2==0)
                ans.push_back(odd[i]);
            else
                ans.push_back(even[i]);
        }
        return ans;
    }
};
```