# 826. Most Profit Assigning Work

**Difficulty:** Medium  
**Topics:** Array, Sorting, 2-Pointer 
**LeetCode:** https://leetcode.com/problems/most-profit-assigning-work/description/   

---

## Solution 1 - Array, Sorting, 2-Pointer

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
    int maxProfitAssignment(vector<int>& difficulty, vector<int>& profit, vector<int>& worker) {
        int ans=0; 
        vector<pair<int,int>> v;
        for(int i=0;i<profit.size();i++)
            v.push_back({difficulty[i],profit[i]});
        sort(v.begin(),v.end());
        sort(worker.begin(),worker.end());
        int i,j,mx=0;
        i=j=0;
        while(i<v.size() && j<worker.size())
        {
            auto [dif,pf] = v[i];
            if(dif<=worker[j])
            {
                mx = max(mx,pf);
                i++;
            }
            else
            {
                ans+=mx;
                j++;
            }

        }
        while(j<worker.size())
        {
            ans+=mx;
            j++;
        }
        return ans;
    }
};
```
