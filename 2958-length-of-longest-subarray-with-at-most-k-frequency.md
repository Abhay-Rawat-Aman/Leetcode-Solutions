# 2958. MLength of Longest Subarray With at Most K Frequency

**Difficulty:** Medium  
**Topics:** Array, Map, 2-Pointer Approch   
**LeetCode:** https://leetcode.com/problems/length-of-longest-subarray-with-at-most-k-frequency/description/   

---

## Solution 1 - Array, Map, 2-Pointer Approch 

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
    int maxSubarrayLength(vector<int>& nums, int k) {
        int ans=0;
        int n=nums.size();
        unordered_map<int,int> m; 
        int i=0,j=0;
        while(i<n)
        {
            m[nums[i]]++;
            while(m[nums[i]]>k)
            {
                m[nums[j]]--;
                j++;
            }
            ans = max(ans,i-j+1);
            i++;
        }
        return ans;
    }
};
```
