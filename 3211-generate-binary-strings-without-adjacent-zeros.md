# 3211. Generate Binary Strings Without Adjacent Zeros

**Difficulty:** Medium  
**Topics:** Recursion, Backtracking   
**LeetCode:** https://leetcode.com/problems/generate-binary-strings-without-adjacent-zeros/description/

---

## Solution 1 - Recursion, Backtracking

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n * 2^n)` |
| Space Complexity | `O(n * 2^n)` |

---

### C++ Code

```cpp
class Solution {
public:
    void Rec(int n,string cur,vector<string> &ans)
    {
        if(n==cur.size())
        {
            ans.push_back(cur);
            return;
        }
        if(cur.size()==0 || cur[cur.size()-1]!='0')
        {
            cur.push_back('0');
            Rec(n,cur,ans);
            cur.pop_back();
        }
        cur.push_back('1');
        Rec(n,cur,ans);

    }
    vector<string> validStrings(int n) {
        vector<string> ans;
        string cur;
        Rec(n,cur,ans); 
        return ans; 
    }
};
```