# 3750. Minimum Number of Flips to Reverse Binary String

**Difficulty:** Easy  
**Topics:** String   
**LeetCode:** https://leetcode.com/problems/minimum-number-of-flips-to-reverse-binary-string/description/   

---

## Solution 1 - String

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Solution {
public:
    int minimumFlips(int n) {
        int ans=0;
        string v;
        int num = n;
        while(num!=0)
        {
            v.push_back(num%2+'0');
            num = num/2;
        }
        n = v.size();
        cout<<v<<" ";
        for(int i=0;i<n/2;i++)
        {
            if(v[i]!=v[n-i-1])
                ans+=2;
        }
        return ans;
    }
};
```