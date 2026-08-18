# 3168. Minimum Number of Chairs in a Waiting Room 

**Difficulty:** Easy  
**Topics:** String   
**LeetCode:**  https://leetcode.com/problems/minimum-number-of-chairs-in-a-waiting-room/description/  

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
    int minimumChairs(string s) {
        int ans;
        int chair = 0;
        for(int i=0;s[i];i++)
        {
            if(s[i]=='E')
                chair++;
            else
                chair--;
            ans = max(ans,chair);
        }
        return ans;
    }
};
```