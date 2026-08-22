# 2429. Minimize XOR

**Difficulty:** Medium  
**Topics:** Bit Manipulation  
**LeetCode:** https://leetcode.com/problems/minimize-xor/description/

---

## Solution 1 - Bit Manipulation

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
    int minimizeXor(int num1, int num2) {
        int ans = 0;
        int setbit = 0;
        while(num2!=0)
        {
            if(num2&1)
                setbit++;
            num2 = num2>>1;
        }
        for(int i=31;i>=0 && setbit>0;i--)
        {
            int set = (num1>>i)&1;
            if((set && setbit) || i<setbit)
            {
                ans = ans | (1<<i);
                setbit--;
            }
        }
        return ans;
    }
};
```