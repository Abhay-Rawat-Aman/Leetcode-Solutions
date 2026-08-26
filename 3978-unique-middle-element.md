# 3978. Unique Middle Element

**Difficulty:** Easy  
**Topics:** Array   
**LeetCode:** https://leetcode.com/problems/unique-middle-element/description/  

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
    bool isMiddleElementUnique(vector<int>& nums) {
        int n = nums.size();
        int dt = nums[n/2];
        for(int i=0;i<n;i++)
        {
            if(dt==nums[i] && i!=n/2)
                return false;
        }
        return true;
    }
};
```