# 3718. Smallest Missing Multiple of K

**Difficulty:** Easy  
**Topics:** Array, Set   
**LeetCode:** https://leetcode.com/problems/smallest-missing-multiple-of-k/description/

---

## Solution 1 - Array, Set

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
    int missingMultiple(vector<int>& nums, int k) {
        unordered_set<int> s; 
        for(int i=0;i<nums.size();i++)
            s.insert(nums[i]);
        int i=1;
        while(s.find(k*i)!=s.end())
            i++;
        return k*i;
    }
};
```