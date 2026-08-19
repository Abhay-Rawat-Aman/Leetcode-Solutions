# 2087. Minimum Cost Homecoming of a Robot in a Grid 

**Difficulty:** Medium  
**Topics:** 2-D Array   
**LeetCode:**  https://leetcode.com/problems/minimum-cost-homecoming-of-a-robot-in-a-grid/description/  

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
    int minCost(vector<int>& startPos, vector<int>& homePos, vector<int>& rowCosts, vector<int>& colCosts) {
        int ans = 0;
        if(startPos[0]<homePos[0])
        {
            for(int i=startPos[0]+1;i<=homePos[0];i++)
                ans+=rowCosts[i];
        }
        else if(startPos[0]>homePos[0])
        {
            for(int i=startPos[0]-1;i>=homePos[0];i--)
                ans+=rowCosts[i];
        }
        if(startPos[1]<homePos[1])
        {
            for(int i=startPos[1]+1;i<=homePos[1];i++)
                ans+=colCosts[i];
        }
        else if(startPos[1]>homePos[1])
        {
            for(int i=startPos[1]-1;i>=homePos[1];i--)
                ans+=colCosts[i];
        }
        return ans; 
    }
};
```