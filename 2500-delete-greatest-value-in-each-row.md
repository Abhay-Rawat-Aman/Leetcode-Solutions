# 2500. Delete Greatest Value in Each Row  

**Difficulty:** Easy  
**Topics:** Array   
**LeetCode:** https://leetcode.com/problems/delete-greatest-value-in-each-row/description/  

---

## Solution 1 - Array  

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n^2(logn))` |
| Space Complexity | `O(1)` |

---

### C++ Code

```cpp
class Solution {
public:
    int deleteGreatestValue(vector<vector<int>>& grid) {
        int ans=0;
        int n = grid.size();
        int m = grid[0].size();
        for(auto i=0;i<n;i++)
            sort(grid[i].begin(),grid[i].end());
        for(int j=0;j<m;j++)
        {
            int mx = INT_MIN;
            for(int i=0;i<n;i++)
                mx = max(grid[i][j],mx);
            ans+=mx;
        }
        return ans;
    }
};
```