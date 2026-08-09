# 2115. Find All Possible Recipes from Given Supplies

**Difficulty:** Medium  
**Topics:** Graph, Topological Sort   
**LeetCode:** https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/description/   

---

## Solution 1 - Graph, Topological Sort

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
    vector<string> findAllRecipes(vector<string>& recipes, vector<vector<string>>& ingredients, vector<string>& supplies) {
        vector<string> ans; 
        unordered_map<string,vector<string>> graph;
        unordered_map<string,int> m;
        for(int i=0;i<recipes.size();i++)
        {   
            for(int j=0;j<ingredients[i].size();j++)
                graph[ingredients[i][j]].push_back(recipes[i]);
            m[recipes[i]] = ingredients[i].size();
        }
        queue<string> q; 
        for(int i=0;i<supplies.size();i++)
            q.push(supplies[i]);
        while(!q.empty())
        {
            string node = q.front();
            for(auto &it:graph[node])
            {
                m[it]--;
                if(m[it]==0)
                {
                    q.push(it);
                    ans.push_back(it);
                }
            }
            q.pop();
        }
        return ans;
    }
};
```
