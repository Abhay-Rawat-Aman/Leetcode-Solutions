# 3112. Minimum Time to Visit Disappearing Nodes

**Difficulty:** Medium  
**Topics:** Graph, Dijkstra Algo, Min Heap  
**LeetCode:** https://leetcode.com/problems/minimum-time-to-visit-disappearing-nodes/description/   

---

## Solution 1 - Graph, Dijkstra Algo, Min Heap

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O((V+E)*logV)` |
| Space Complexity | `O(V+E)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<int> minimumTime(int n, vector<vector<int>>& edges, vector<int>& disappear) {
        vector<vector<pair<int,int>>> graph(n);
        for(int i=0;i<edges.size();i++)
        {
            graph[edges[i][0]].push_back({edges[i][1],edges[i][2]});
            graph[edges[i][1]].push_back({edges[i][0],edges[i][2]});
        }
        vector<int> dist(n,INT_MAX);
        priority_queue<pair<int,int>,
                    vector<pair<int,int>>,
                    greater<pair<int,int>>> pq;
        pq.emplace(0,0);
        dist[0]=0;
        while(!pq.empty())
        {
            int d = pq.top().first;
            int u = pq.top().second;
            pq.pop();
            if(d>dist[u])
                continue;
            for(auto &it:graph[u])
            {
                int v = it.first;
                int w = it.second;
                if(dist[u]+w<dist[v] && dist[u]+w<disappear[v])
                {
                    dist[v] = dist[u]+w;
                    pq.emplace(dist[v],v);
                }
            }
        }
        for(int i=0;i<n;i++)
            if(dist[i]==INT_MAX)
                dist[i] = -1;
        return dist;
    }
};
```
