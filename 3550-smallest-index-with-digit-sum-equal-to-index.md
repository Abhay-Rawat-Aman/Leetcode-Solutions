# 3550. Smallest Index With Digit Sum Equal to Index  

**Difficulty:** Easy  
**Topics:** Array, Math   
**LeetCode:** https://leetcode.com/problems/smallest-index-with-digit-sum-equal-to-index/description/  

---

## Solution 1 - Array, Math

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
    int smallestIndex(vector<int>& nums) {
        for(int i=0;i<nums.size();i++)
        {
            int sum = 0;
            while(nums[i]!=0)
            {
                sum+=(nums[i]%10);
                nums[i] = nums[i]/10;
            }
            if(sum==i)
                return i;
        }
        return -1;
    }
};
```