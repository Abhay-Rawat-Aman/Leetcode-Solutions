# 3884. First Matching Character From Both Ends

**Difficulty:** Easy  
**Topics:** String   
**LeetCode:** https://leetcode.com/problems/first-matching-character-from-both-ends/description/   

---

## Solution 1 - String

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
    int firstMatchingIndex(string s) {
        int n = s.size();
        for(int i=0;i<=n/2;i++)
            if(s[i]==s[n-i-1])
                return i;
        return -1;
    }
};
```