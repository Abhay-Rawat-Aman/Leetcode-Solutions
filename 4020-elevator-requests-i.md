# 4020.  Elevator Requests I

**Difficulty:** Easy  
**Topics:** Array   
**LeetCode:** https://leetcode.com/problems/elevator-requests-i/description/

---

## Solution 1 - Array

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
    int elevatorRequests(int n, vector<int>& requests) {
        int ans = 0;
        int data = 0;
        for(auto &it:requests)
        {
            ans+=(abs(data-it));
            data = it;
        }
        return ans; 
    }
};
```