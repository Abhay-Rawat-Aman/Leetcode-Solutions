# 3760. Maximum Substrings With Distinct Start

**Difficulty:** Medium  
**Topics:** Array  
**LeetCode:** https://leetcode.com/problems/maximum-substrings-with-distinct-start/description/   

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
    int maxDistinct(string s) {
        int ans=0;
        vector<int> v(26,0);
        for(int i=0;s[i];i++)
            v[s[i]-'a']=1;
        for(int i=0;i<26;i++)
            ans+=v[i];
        return ans;
    }
};
```
