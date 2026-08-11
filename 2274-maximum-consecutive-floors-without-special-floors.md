# 2274. Maximum Consecutive Floors Without Special Floors

**Difficulty:** Medium  
**Topics:** Array, Sort   
**LeetCode:** https://leetcode.com/problems/maximum-consecutive-floors-without-special-floors/   

---

## Solution 1 - Array, Sort

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(nlogn)` |
| Space Complexity | `O(1)` |

---

### C++ Code

```cpp
class Solution {
public:
    int maxConsecutive(int bottom, int top, vector<int>& special) {
        sort(special.begin(),special.end());
        int ans = special[0]-bottom;
        for(int i=1;i<special.size();i++)
            ans = max(ans,special[i]-special[i-1]-1);
        ans = max(ans,top-special[special.size()-1]);
        return ans;
    }
};
```
