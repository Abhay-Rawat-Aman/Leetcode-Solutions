# 3931. Check Adjacent Digit Differences 

**Difficulty:** Easy  
**Topics:** String   
**LeetCode:**  https://leetcode.com/problems/check-adjacent-digit-differences/description/  

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
    bool isAdjacentDiffAtMostTwo(string s) {
        for(int i=1;i<s.size();i++)
        {
            int diff = abs(s[i]-s[i-1]);
            if(diff>2)
                return false;
        }
        return true;
    }
};
```