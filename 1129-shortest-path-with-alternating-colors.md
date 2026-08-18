# 1129. Shortest Path with Alternating Colors 

**Difficulty:** Medium  
**Topics:** Graph, BFS   
**LeetCode:**  https://leetcode.com/problems/shortest-path-with-alternating-colors/  

---

## Solution 1 - Graph, BFS

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
    vector<int> shortestAlternatingPaths(int n, vector<vector<int>>& redEdges, vector<vector<int>>& blueEdges) {
        vector<int> ans(n,INT_MAX);
        vector<pair<bool,bool>> visited(n,{false,false});
        vector<vector<int>> redGraph(n),blueGraph(n);
        for(auto &it:redEdges)
            redGraph[it[0]].push_back(it[1]);
        for(auto &it:blueEdges)
            blueGraph[it[0]].push_back(it[1]);
        queue<tuple<int,char,int>> q;
        q.push({0,'R',0});
        q.push({0,'B',0});
        visited[0].first = visited[0].second = true;
        ans[0] = 0;
        while(!q.empty())
        {
            auto [node,color,level] = q.front();
            q.pop();
            ans[node] = min(ans[node],level);
            if(color=='R')
            {
                for(auto &it:blueGraph[node])
                {
                    if(!visited[it].second)
                    {
                        visited[it].second=true;
                        q.push({it,'B',level+1});
                    }
                }
            }
            else 
            {
                for(auto &it:redGraph[node])
                {
                    if(!visited[it].first)
                    {
                        visited[it].first=true;
                        q.push({it,'R',level+1});
                    }
                }
            }
        }
        for(int i=0;i<n;i++)
            if(ans[i]==INT_MAX)
                ans[i]=-1;
        return ans; 
    }
};
```