# 3643. Flip Square Submatrix Vertically  

**Difficulty:** Easy  
**Topics:** 2-D Array   
**LeetCode:** https://leetcode.com/problems/flip-square-submatrix-vertically/description/  

---

## Solution 1 - 2-D Array

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
    vector<vector<int>> reverseSubmatrix(vector<vector<int>>& grid, int x, int y, int k) {
        int i=x;
        int j=x+k;
        while(i<j)
        {
            for(int index=0;index<k;index++)
            {
                int temp = grid[i][y+index];
                grid[i][y+index] = grid[j-1][y+index];
                grid[j-1][y+index] = temp; 
            }
            i++;
            j--;
        }
        return grid;
    }
};
```