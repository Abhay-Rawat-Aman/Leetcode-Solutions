# 3895. Count Digit Appearances

**Difficulty:** Medium  
**Topics:** Array, Maths  
**LeetCode:** https://leetcode.com/problems/count-digit-appearances/description/  

---

## Solution - Maths 

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
    int countDigitOccurrences(vector<int>& nums, int digit) {
        int ans=0; 
        for(int i=0;i<nums.size();i++)
        {
            int num = nums[i];
            while(num!=0)
            {
                if(num%10 == digit)
                    ans++;
                num = num/10;
            }
        }
        return ans; 
    }
};
```