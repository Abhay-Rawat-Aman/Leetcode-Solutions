# 3925. Concatenate Array With Reverse

**Difficulty:** Easy  
**Topics:** Array  
**LeetCode:** https://leetcode.com/problems/concatenate-array-with-reverse/description/  

---

## Solution - Array 

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n)` |
| Space Complexity | `O(1)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<int> concatWithReverse(vector<int>& nums) {
        int n = nums.size();
        vector<int> ans(n+n,0); 
        for(int i=0;i<nums.size();i++)
        {
            ans[i] = nums[i];
            ans[n+i] = nums[n-i-1];
        }
        return ans;
    }
};
```