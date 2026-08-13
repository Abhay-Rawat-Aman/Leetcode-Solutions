# 224. Basic Calculator  

**Difficulty:** Hard  
**Topics:** String, Stack  
**LeetCode:** https://leetcode.com/problems/basic-calculator/description/  

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
    int calculate(string s) {
        stack<pair<int,int>> st;
        int ans=0,sign=1;
        unsigned int val=0;
        for(int i=0;i<s.size();i++)
        {
            if(s[i]>='0' && s[i]<='9')
                val = val*10+(s[i]-'0');
            else
            {
                ans = ans + val*sign;
                val=0;
            }
            if(s[i]=='+')
                sign=1;
            else if(s[i]=='-')
                sign=-1;
            else if(s[i]=='(')
            {
                st.push({ans,sign});
                ans=0;
                sign=1;
            }
            else if(s[i]==')')
            {
                auto [tp,sn] = st.top();
                st.pop();
                ans = tp + sn * ans;
                val=0;
            }
        }
        ans = ans+sign*val;
        return ans;
    }

};
```