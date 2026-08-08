# 2295. Replace Elements in an Array   

**Difficulty:** Medium  
**Topics:** Array, Map  
**LeetCode:** https://leetcode.com/problems/replace-elements-in-an-array/description/ 

---

## Solution 1 - Map and Array

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
    vector<int> arrayChange(vector<int>& nums, vector<vector<int>>& operations) {
        unordered_map<int,int> m;
        for(int i=0;i<nums.size();i++)
            m[nums[i]] = i;
        for(int i=0;i<operations.size();i++)
        {
            auto data = operations[i];
            auto index = m[data[0]];
            m.erase(data[0]);
            m[data[1]] = index;
            nums[index] = data[1];
;        }
        return nums;
    }
};
```