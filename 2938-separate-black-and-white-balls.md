# 2938. Separate Black and White Balls   

**Difficulty:** Medium  
**Topics:** String  
**LeetCode:** https://leetcode.com/problems/separate-black-and-white-balls/description/  

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
    long long minimumSteps(string s) {
        long long ans=0;
        int black = -1;
        for(int i=0;s[i];i++)
        {
            if(s[i]=='0')
            {
                black++;
                ans+= i-black;
            }
        }
        return ans;
    }
};
```