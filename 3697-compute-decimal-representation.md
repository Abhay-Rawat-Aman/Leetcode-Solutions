# 3697. Compute Decimal Representation  

**Difficulty:** Easy  
**Topics:** Array, Math   
**LeetCode:** https://leetcode.com/problems/compute-decimal-representation/description/  

---

## Solution 1 - Array, Math

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
    vector<int> decimalRepresentation(int n) {
        vector<int> ans;
        unsigned int s = 1;
        while(n!=0)
        {
            int r = n%10;
            n = n/10;
            if(r!=0)
            ans.push_back(s*r);
            s*=10;
        }
        int ansSize = ans.size();
        for(int i=0;i<ansSize/2;i++)
        {
            int temp = ans[i];
            ans[i] = ans[ansSize-1-i];
            ans[ansSize-1-i] = temp;
        } 
        return ans;
    }
};
```