# 994. Rotting Oranges

**Difficulty:** Medium  
**Topics:** Graph, BFS   
**LeetCode:** https://leetcode.com/problems/rotting-oranges/description/

---

## Solution 1 - Graph, BFS

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n*m)` |
| Space Complexity | `O(n*m)` |

---

### C++ Code

```cpp
class Solution {
public:
    int orangesRotting(vector<vector<int>>& grid) {
        int ans = 0;
        int n = grid.size();
        int m = grid[0].size();
        queue<tuple<int,int,int>> q;
        vector<pair<int,int>> v = {{0,1},{0,-1},{1,0},{-1,0}};
        vector<vector<bool>> visited(n,vector<bool>(m,false));
        int freshOranges = 0;
        //find rotten oranges 
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                if(grid[i][j]==2)
                    q.push({i,j,0});
                else if(grid[i][j]==1)
                    freshOranges++;
            }
        }
        //apply bfs for caluating the min time 
        while(!q.empty())
        {
            auto [row,col,level] = q.front();
            ans = max(ans,level);
            q.pop();
            for(int i=0;i<4;i++)
            {
                int nrow = row+v[i].first;
                int ncol = col+v[i].second;
                if(nrow<0 || ncol<0 || nrow==n || ncol==m || visited[nrow][ncol] || grid[nrow][ncol]!=1) 
                    continue;
                visited[nrow][ncol] = true;
                freshOranges--;
                q.push({nrow,ncol,level+1});
            }
        }
        return freshOranges==0?ans:-1;
    }
};
```