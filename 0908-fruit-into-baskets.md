# 908. Fruit Into Baskets  

**Difficulty:** Medium  
**Topics:** Array, Map, 2-Pointer   
**LeetCode:**https://leetcode.com/problems/fruit-into-baskets/description/ 

---

## Solution 1 - Array, Map, 2-Pointer

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
    int totalFruit(vector<int>& fruits) {
        int ans=0;
        int i = 0,j=0;
        unordered_map<int,int> m; 
        while(j<fruits.size())
        {
            m[fruits[j]]++;
            while(m.size()>2)
            {
                m[fruits[i]]--;
                if(m[fruits[i]]==0)
                    m.erase(fruits[i]);
                i++;
            }
            ans = max(ans,j-i+1);
            j++;
        }
        return ans;
    }
};
```