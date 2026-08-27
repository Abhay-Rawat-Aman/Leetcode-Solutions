# 3765. Complete Prime Number  

**Difficulty:** Medium  
**Topics:** Array, Set   
**LeetCode:** https://leetcode.com/problems/complete-prime-number/description/  

---

## Solution 1 - Array, Set  

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(logn * sqrt(n))` |
| Space Complexity | `O(logn)` |

---

### C++ Code

```cpp
class Solution {
    private: 
    bool Prime(int num)
    {
        if(num==1)
            return false;
        for(int i=2;i<=sqrt(num);i++)
        {
            if(num%i==0)
                return false;
        }
        return true;
    }
public:
    bool completePrime(int num) {
        unordered_set<int> st;
        st.insert(num);
        long int s = 10,n = num;
        while(n%s!=num)
        {
            st.insert(n/s);
            st.insert(n%s);
            s*=10;
        }
        for(auto &it:st){
            if(!Prime(it))
                return false;
        }
        return true;
    }
};
```