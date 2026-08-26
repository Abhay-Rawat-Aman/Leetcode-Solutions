# 3683. Earliest Time to Finish One Task

**Difficulty:** Easy  
**Topics:** Array   
**LeetCode:** https://leetcode.com/problems/earliest-time-to-finish-one-task/description/  

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
    int earliestTime(vector<vector<int>>& tasks) {
        int ans = INT_MAX;
        for(int i=0;i<tasks.size();i++)
            ans = min(ans,tasks[i][0]+tasks[i][1]);
        return ans; 
    }
};
```