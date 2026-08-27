# 3604. Minimum Time to Reach Destination in Directed Graph  

**Difficulty:** Medium  
**Topics:** Graph, Dijkstra Algo   
**LeetCode:** https://leetcode.com/problems/minimum-time-to-reach-destination-in-directed-graph/description/  

---

## Solution 1 - Graph, Dijkstra Algo  

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(E logE)` |
| Space Complexity | `O(V+E)` |

---

### C++ Code

```cpp
class Solution {
public:
    int minTime(int n, vector<vector<int>>& edges) {
        int ans = 0;
        vector<vector<tuple<int,int,int>>> graph(n);
        for(auto &it:edges)
            graph[it[0]].push_back({it[1],it[2],it[3]});
        priority_queue<pair<int,int>,
                vector<pair<int,int>>,
                greater<>> pq;
        pq.emplace(0,0);
        vector<int> time(n,INT_MAX);
        time[0]=0;
        while(!pq.empty())
        {
            auto [curTime,node] = pq.top();
            if(node==n-1)
                break;
            pq.pop();
            for(auto &it:graph[node])
            {
                auto [neb,start,end] = it;
                if(curTime<=start)
                {
                    if(time[neb]>start)
                    {
                        time[neb] = start+1;
                        pq.emplace(start+1,neb);
                    }
                }
                else if(curTime>start && curTime<=end)
                {
                    if(time[neb]>curTime+1)
                    {
                        time[neb] = curTime+1;
                        pq.emplace(curTime+1,neb);
                    }
                }
            }
        }
        if(time[n-1]==INT_MAX)
            return -1;
        return time[n-1]; 
    }
};
```