# 3842. First Element with Unique Frequency  

**Difficulty:** Medium  
**Topics:** Array, Map, Counting   
**LeetCode:** https://leetcode.com/problems/first-element-with-unique-frequency/description/  

---

## Solution 1 - Array, Map, Counting 

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
    int firstUniqueFreq(vector<int>& nums) {
        unordered_map<int,int> freq;
        for(int i=0;i<nums.size();i++)
            freq[nums[i]]++;
        unordered_map<int,int> mp; 
        for(auto &it:freq)
            mp[it.second]++;
        for(int i=0;i<nums.size();i++)
        {
            int f = freq[nums[i]];
            if(mp[f]==1)
                return nums[i];
        }
        return -1;
    }
};
```