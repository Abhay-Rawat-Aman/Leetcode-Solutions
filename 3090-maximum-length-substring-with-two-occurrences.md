# 3112. Maximum Length Substring With Two Occurrences

**Difficulty:** Easy  
**Topics:** String, 2 Pointer, Map  
**LeetCode:** https://leetcode.com/problems/maximum-length-substring-with-two-occurrences/description/   

---

## Solution 1 - String, 2-Pointer, Map

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
    int maximumLengthSubstring(string s) {
        int ans = 0;
        unordered_map<int,int> m; 
        int i=0,j=0;
        while(j<s.size())
        {
            char ch=s[j];
            m[s[j]]++;
            while(m[s[j]]>2)
            {
                m[s[i]]--;
                i++;
            }
            ans = max(ans,j-i+1);
            j++;
        }
        return ans;
    }
};
```
