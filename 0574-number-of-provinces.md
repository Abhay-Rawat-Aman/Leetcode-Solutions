# 574. Number of Provinces

**Difficulty:** Easy  
**Topics:** Graph, BFS, DFS   
**LeetCode:** https://leetcode.com/problems/number-of-provinces/description/

---

## Solution 1 - Graph, BFS

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n+e)` |
| Space Complexity | `O(n+e)` |

---

### C++ Code

```cpp
class Solution {
public:
    void bfs(int node, vector<bool> &visited, vector<vector<int>> &graph)
    {
        queue<int> q;
        q.push(node);
        while(!q.empty())
        {
            int n = q.front();
            q.pop();
            for(auto &it:graph[n])
            {
                if(!visited[it])
                {
                    visited[it]=true;
                    q.push(it);
                }
            }
        }
    }
    int findCircleNum(vector<vector<int>>& isConnected) {
        int n = isConnected.size();
        vector<vector<int>> v(n);
        int cnt=0;
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<n;j++)
            {
                if(i!=j && isConnected[i][j]==1)
                {
                    v[i].push_back(j);
                    v[j].push_back(i);
                }
            }
        }
        vector<bool> visited(n,false);
        for(int i=0;i<n;i++)
        {
            if(!visited[i])
            {
                bfs(i,visited,v);
                cnt++;
            }
        }
        return cnt;
    }
};
```

---

## Solution 2 - Graph, DFS

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n+e)` |
| Space Complexity | `O(n+e)` |

---

### C++ Code

```cpp
class Solution {
public:
    void dfs(int node, vector<bool> &visited, vector<vector<int>> &graph)
    {
        visited[node]=true;
        for(auto &it:graph[node])
        {
            if(!visited[it])
                dfs(it,visited,graph);
        }
    }
    int findCircleNum(vector<vector<int>>& isConnected) {
        int n = isConnected.size();
        vector<vector<int>> v(n);
        int cnt=0;
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<n;j++)
            {
                if(i!=j && isConnected[i][j]==1)
                {
                    v[i].push_back(j);
                    v[j].push_back(i);
                }
            }
        }
        vector<bool> visited(n,false);
        for(int i=0;i<n;i++)
        {
            if(!visited[i])
            {
                dfs(i,visited,v);
                cnt++;
            }
        }
        return cnt;
    }
};
```