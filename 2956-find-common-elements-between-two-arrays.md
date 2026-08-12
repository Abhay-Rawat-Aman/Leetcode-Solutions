# 2956. Find Common Elements Between Two Arrays

**Difficulty:** Easy  
**Topics:** Array, Set   
**LeetCode:** https://leetcode.com/problems/find-common-elements-between-two-arrays/description/   

---

## Solution 1 - Array, Set 

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
    vector<int> findIntersectionValues(vector<int>& nums1, vector<int>& nums2) {
        unordered_set<int> s1,s2;
        for(auto &it:nums1)
            s1.insert(it);
        for(auto &it:nums2)
            s2.insert(it);
        vector<int> ans(2,0);
        for(auto &it:nums1)
        {
            if(s2.find(it)!=s2.end())
                ans[0]+=1;
        }
        for(auto &it:nums2)
        {
            if(s1.find(it)!=s1.end())
                ans[1]+=1;
        }
        return ans;
    }
};
```
