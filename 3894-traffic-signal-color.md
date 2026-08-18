# 3894. Traffic Signal Color

**Difficulty:** Easy  
**Topics:** String 
**LeetCode:** https://leetcode.com/problems/traffic-signal-color/description/   

---

## Solution 1 - String

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(1)` |
| Space Complexity | `O(1)` |

---

### C++ Code

```cpp
class Solution {
public:
    string trafficSignal(int timer) {
        if(timer==0)
            return "Green";
        else if(timer == 30)
            return "Orange";
        else if(timer>30 && timer<=90)
            return "Red";
        return "Invalid";
    }
};
```
