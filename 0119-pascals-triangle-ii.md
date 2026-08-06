# 119. Pascal's Triangle II

**Difficulty:** Easy  
**Topics:** Array, DP   
**LeetCode:** https://leetcode.com/problems/pascals-triangle-ii/description/ 

---

## Solution 1 - Tabulation with space optimization

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n^2)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<int> getRow(int rowIndex) {
        vector<int> prev;
        prev.push_back(1);
        if(rowIndex == 0)
            return prev;
        for(int row = 0;row<=rowIndex;row++)
        {
            vector<int> cur(row+1,1); 
            for(int col=0;col<=row;col++)
            {
                if(col==0 || col==row)
                    cur[col] = 1;
                else
                    cur[col] = prev[col] + prev[col-1];
            }
            prev = cur;
        }
        return prev;
    }
};
```