# 3866. First Unique Even Element  

**Difficulty:** Easy  
**Topics:** Array, Map   
**LeetCode:** https://leetcode.com/problems/first-unique-even-element/description/  

---

## Solution 1 - Array, Map

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Solution {
public:
    int firstUniqueEven(vector<int>& nums) {
        unordered_map<int,int> m;
        for(int i=0;i<nums.size();i++)
            m[nums[i]]++;
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]%2==0 && m[nums[i]]==1)
                return nums[i];
        }
        return -1;
    }
};
```