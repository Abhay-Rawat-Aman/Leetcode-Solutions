# 3813. Vowel-Consonant Score  

**Difficulty:** Easy  
**Topics:** Array, String   
**LeetCode:** https://leetcode.com/problems/vowel-consonant-score/description/ 

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
    int vowelConsonantScore(string s) {
        int ans=0;
        int v = 0,c = 0;
        for(int i=0;s[i];i++)
            if(s[i]=='a' || s[i]=='e' || s[i]=='i' || s[i]=='o' || s[i]=='u')
                v++;
            else if(!(s[i]>='0' && s[i]<='9') && s[i]!=' ')
                c++;
        if(c>0)
            ans = v/c;
        return ans;
    }
};
```