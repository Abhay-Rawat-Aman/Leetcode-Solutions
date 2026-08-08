# 3731. Find Missing Elements

**Difficulty:** Easy  
**Topics:** Array   
**LeetCode:** https://leetcode.com/problems/find-missing-elements/description/   

---

## Solution 1 - Array and Set

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
    vector<int> findMissingElements(vector<int>& nums) {
        vector<int> ans; 
        int mx = INT_MIN;
        int mn = INT_MAX;
        unordered_set<int> s;
        for(int i=0;i<nums.size();i++)
        {
            mx = max(mx,nums[i]);
            mn = min(mn,nums[i]);
            s.insert(nums[i]);
        }
        for(int i=mn;i<=mx;i++)
            if(s.find(i)==s.end())
                ans.push_back(i);
        return ans;   
    }
};
```