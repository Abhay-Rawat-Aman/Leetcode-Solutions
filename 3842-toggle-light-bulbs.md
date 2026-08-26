# 3842. Toggle Light Bulbs

**Difficulty:** Easy  
**Topics:** Array, Map   
**LeetCode:** https://leetcode.com/problems/toggle-light-bulbs/description/  

---

## Solution 1 - Array, Map

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(nlogn)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<int> toggleLightBulbs(vector<int>& bulbs) {
        map<int,int> m;
        vector<int> ans; 
        for(int i=0;i<bulbs.size();i++)
            m[bulbs[i]]++;
        for(auto &it:m)
        {
            if(it.second%2==1)
                ans.push_back(it.first);
        }
        return ans;
    }
};
```