# 2643. Row With Maximum Ones

**Difficulty:** Easy  
**Topics:** Array   
**LeetCode:** https://leetcode.com/problems/row-with-maximum-ones/description/  

---

## Solution 1 - Array

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
    vector<int> rowAndMaximumOnes(vector<vector<int>>& mat) {
        vector<int> ans(2,0);
        int n = mat.size();
        int m = mat[0].size();
        for(int i=0;i<n;i++)
        {
            int sum = 0;
            for(int j=0;j<m;j++)
            {
                if(mat[i][j]==1)
                    sum+=1;
            }
            if(sum>ans[1])
            {
                ans[1] = sum;
                ans[0] = i;
            }
        } 
        return ans;
    }
};
```