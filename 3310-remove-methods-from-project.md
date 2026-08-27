# 3310. Remove Methods From Project  

**Difficulty:** Medium  
**Topics:** Graph, DFS   
**LeetCode:** https://leetcode.com/problems/remove-methods-from-project/description/  

---

## Solution 1 - Graph, DFS  

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(V+E)` |
| Space Complexity | `O(V+E)` |

---

### C++ Code

```cpp
class Solution {
    private:
    void DFS(int node,vector<vector<int>> &graph,vector<bool> &visited)
    {
        visited[node] = true;
        for(auto &it:graph[node])
        {
            if(!visited[it])
                DFS(it,graph,visited);
        }
    }
public:
    vector<int> remainingMethods(int n, int k, vector<vector<int>>& invocations) {
        vector<int> ans;
        vector<vector<int>> graph(n);
        for(auto &it:invocations)
            graph[it[0]].push_back(it[1]);
        vector<bool> visited(n,false);
        DFS(k,graph,visited);
        int isConnected = false;
        for(int i=0;i<n;i++)
        {
            if(visited[i])
                continue;
            for(auto &it:graph[i])
            {
                if(visited[it])
                {
                    isConnected = true;
                    break;
                }
            }
        }
        if(isConnected)
        {
            for(int i=0;i<n;i++)
                ans.push_back(i);
        }
        else 
        {
            for(int i=0;i<n;i++)
            {
                if(!visited[i])
                    ans.push_back(i);
            }
        }
        return ans; 
    }
};
```