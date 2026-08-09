# 71. Simplify Path

**Difficulty:** Medium  
**Topics:** String, Stack   
**LeetCode:** https://leetcode.com/problems/simplify-path/   

---

## Solution 1 - String, Stack

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
    string simplifyPath(string path) {
        string ans;
        string s;
        stack<string> st;
        for(int i=1;path[i];i++)
        {
            if(path[i]=='/')
            {
                if(s=="."){}
                else if(s=="..")
                {
                    if(!st.empty())
                    st.pop();
                }
                else if(!s.empty())
                    st.push(s);
                s="";
            }
            else
                s.push_back(path[i]);
        }
        if(s=="."){}
        else if(s=="..")
        {
            if(!st.empty())
            st.pop();
        }
        else if(!s.empty())
            st.push(s);
        if(st.empty())
            return "/";
        while(!st.empty())
        {
            ans = '/'+st.top()+ans;
            st.pop();
        }
        return ans;
    }
};
```
