# 1424. Diagonal Traverse II

**Difficulty:** Medium  
**Topics:** 2-D Array, Map  
**LeetCode:** https://leetcode.com/problems/diagonal-traverse-ii/description/   

---

## Solution 1 - 2-D Array, Map

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n*m)` |
| Space Complexity | `O(n*m)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<int> findDiagonalOrder(vector<vector<int>>& nums) {
        vector<int> ans;
        unordered_map<int,vector<int>> m;
        int mx = 0;
        for(int i=0;i<nums.size();i++)
        {
            for(int j=0;j<nums[i].size();j++)
            {
                m[i+j].push_back(nums[i][j]);
                mx=max(mx,i+j);
            }
        }
        int sum = 0;
        while(sum<=mx)
        {
            for(int i=m[sum].size()-1;i>=0;i--)
                ans.push_back(m[sum][i]);
            sum++;
        }
        return ans; 
    }
};
```
