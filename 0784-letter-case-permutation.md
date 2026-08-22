# 784. Letter Case Permutation

**Difficulty:** Medium  
**Topics:** Recursion, Backtracking   
**LeetCode:** https://leetcode.com/problems/letter-case-permutation/description/

---

## Solution 1 - Recursion, Backtracking

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n* 2^n)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Solution {
public:
    void Rec(int index,string cur,string s,vector<string> &ans)
    {
        if(index==s.size())
        {
            ans.push_back(cur);
            return;
        }
        if(s[index]>='0' && s[index]<='9')
        {
            cur.push_back(s[index]);
            Rec(index+1,cur,s,ans);
            cur.pop_back();
        }
        else 
        {
            cur.push_back(s[index]);
            Rec(index+1,cur,s,ans);
            cur.pop_back();
            int d = (s[index]>='A' && s[index]<='Z')?32:-32;
            cur.push_back(s[index]+d);
            Rec(index+1,cur,s,ans);
        }
    }
    vector<string> letterCasePermutation(string s) {
        vector<string> ans;
        int index=0;
        string cur;
        Rec(index,cur,s,ans);
        return ans;
    }
};
```