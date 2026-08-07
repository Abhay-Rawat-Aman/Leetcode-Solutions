# 3798. Largest Even Number  

**Difficulty:** Easy  
**Topics:** Array, String   
**LeetCode:** https://leetcode.com/problems/largest-even-number/description/ 

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
    string largestEven(string s) {
        int lastocc = -1;
        for(int i=s.size()-1;i>=0;i--)
        {
            if(s[i]=='2')
            {
                lastocc = i;
                break;
            }
        }
        string ans; 
        for(int i=0;i<=lastocc;i++)
            ans.push_back(s[i]);
        return ans; 
    }
};
```