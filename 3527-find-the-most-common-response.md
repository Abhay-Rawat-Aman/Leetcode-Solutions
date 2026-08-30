# 3527. Find the Most Common Response  

**Difficulty:** Medium  
**Topics:** String, Map, Set   
**LeetCode:** https://leetcode.com/problems/find-the-most-common-response/description/  

---

## Solution 1 - String, Map, Set 

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n*m)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Solution {
public:
    string findCommonResponse(vector<vector<string>>& responses) {
        unordered_map<string,int> m;
        for(auto &row:responses)
        {
            unordered_set<string> s;
            for(auto &it:row)
            {
                if(s.find(it)==s.end())
                {
                    m[it]++;
                    s.insert(it);
                }
            }
        }
        string ans; 
        int mx = 0; 
        for(auto &it:m)
        {
            auto [data,count] = it;
            if(count>mx)
            {
                mx = count; 
                ans = data;
            }
            else if(count == mx && data<ans)
                ans = data;
        }
        return ans; 
    }
};
```