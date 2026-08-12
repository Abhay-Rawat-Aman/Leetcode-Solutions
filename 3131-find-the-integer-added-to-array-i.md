# 3131. Find the Integer Added to Array I  

**Difficulty:** Easy  
**Topics:** Array   
**LeetCode:** https://leetcode.com/problems/find-the-integer-added-to-array-i/description/ 

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
    int addedInteger(vector<int>& nums1, vector<int>& nums2) {
        int mn1 = INT_MAX;
        int mn2 = INT_MAX;
        for(int i=0;i<nums1.size();i++)
        {
            mn1 = min(mn1,nums1[i]);
            mn2 = min(mn2,nums2[i]);   
        }
        return mn2-mn1;
    }
};
```