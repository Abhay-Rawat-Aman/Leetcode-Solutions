# 3295. Report Spam Message  

**Difficulty:** Medium  
**Topics:** Array   
**LeetCode:**https://leetcode.com/problems/report-spam-message/description/ 

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
    bool reportSpam(vector<string>& message, vector<string>& bannedWords) {
        unordered_set<string> s; 
        for(auto &it:bannedWords)
            s.insert(it);
        int count = 0;
        for(auto &word:message)
        {
            if(s.find(word)!=s.end())
                count++;
            if(count>1)
                return true;
        }
        return false;
    }
};
```