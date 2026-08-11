# 128. Longest Consecutive Sequence

**Difficulty:** Medium  
**Topics:** Array, Set   
**LeetCode:** https://leetcode.com/problems/longest-consecutive-sequence/description/   

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
    int longestConsecutive(vector<int>& nums) {
        if(nums.size()<=1)
            return nums.size();
        int ans=1;
        int prev = 1;
        unordered_set<int> s; 
        for(auto &it:nums)
            s.insert(it);
        for(auto &num:s)
        {
            int consecutive = 0;
            int n = num-1;
            while(s.find(n)!=s.end())
            {
                consecutive++;
                s.erase(n);
                n--;
            }
            n = num+1;
            while(s.find(n)!=s.end())
            {
                consecutive++;
                s.erase(n);
                n++;
            }
            ans = max(ans,consecutive+1); 
        }
        return ans;
    }
};
```
