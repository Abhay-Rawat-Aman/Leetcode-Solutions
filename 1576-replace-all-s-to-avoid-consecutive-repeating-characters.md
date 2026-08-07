# 1576. Replace All ?'s to Avoid Consecutive Repeating Characters

**Difficulty:** Easy  
**Topics:** String   
**LeetCode:** https://leetcode.com/problems/replace-all-s-to-avoid-consecutive-repeating-characters/description/ 

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
    string modifyString(string s) {
        vector<int> v(26,0);
        for(int i=0;s[i];i++)
        {
            if(s[i]!='?')
                continue;
            if(i-1>=0)
                v[s[i-1]-'a'] = 1;
            if(i+1<s.size() && s[i+1]!='?')
                v[s[i+1]-'a'] = 1;
            if(v[0]==0)
                s[i] = 'a';
            else if (v[1]==0)
                s[i] = 'b';
            else 
                s[i] = 'c';
            v[0] = v[1] = v[2] = 0;
        }
        return s;
    }
};
```