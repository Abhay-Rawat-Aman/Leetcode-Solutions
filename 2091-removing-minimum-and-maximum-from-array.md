# 2091. Removing Minimum and Maximum From Array

**Difficulty:** Medium  
**Topics:** Array  
**LeetCode:** https://leetcode.com/problems/removing-minimum-and-maximum-from-array/description/   

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
    int minimumDeletions(vector<int>& nums) {
        if(nums.size()<3)
            return nums.size();
        int mn = nums[0],mx = nums[0],indexmn = 0,indexmx = 0;
        for(int i=1;i<nums.size();i++)
        {
            if(mx<nums[i])
            {
                mx = nums[i];
                indexmx=i;
            }
            else if(mn>nums[i])
            {
                mn = nums[i];
                indexmn=i;
            }
        }
        int i1 = min(indexmx,indexmn);
        int i2 = max(indexmx,indexmn);
        int n = nums.size();
        return min(i1+n-i2+1,min(n-i1,i2+1));
    }
};
```
