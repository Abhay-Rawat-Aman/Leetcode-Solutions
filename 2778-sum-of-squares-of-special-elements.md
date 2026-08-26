# 2778. Sum of Squares of Special Elements 

**Difficulty:** Easy  
**Topics:** Array   
**LeetCode:** https://leetcode.com/problems/sum-of-squares-of-special-elements/description/

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
    int sumOfSquares(vector<int>& nums) {
        int n = nums.size();
        int ans = 0;
        for(int i=0;i<n;i++)
        {
            if(n%(i+1)==0)
                ans+=nums[i]*nums[i];
        }
        return ans; 
    }
};
```