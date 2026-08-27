# 3770. Largest Prime from Consecutive Prime Sum  

**Difficulty:** Medium  
**Topics:** Array   
**LeetCode:** https://leetcode.com/problems/largest-prime-from-consecutive-prime-sum/description/  

---

## Solution 1 - Array  

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n*(sqrt(n)))` |
| Space Complexity | `O(1)` |

---

### C++ Code

```cpp
class Solution {
private : 
    bool prime(int n)
    {
        for(int i=2;i*i<=n;i++)
        {
            if(n%i==0)
                return false;
        }
        return true;
    }
public:
    int largestPrime(int n) {
        int sum=0; 
        int ans = 0;
        if(n==1)
            return 0;
        for(int i=2;i<=n && (sum+i)<=n;i++)
        {
            if(prime(i) )
                sum+=i;
            if(prime(sum))
                ans = sum;
        }
        return ans; 
    }
};
```