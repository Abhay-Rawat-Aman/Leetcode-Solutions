# 733. Flood Fill

**Difficulty:** Easy  
**Topics:** Graph, BFS, DFS   
**LeetCode:** https://leetcode.com/problems/flood-fill/description/

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
    void bfs(vector<vector<int>> &image,int sr,int sc,int color)
    {
        int n = image.size();
        int m = image[0].size();
        int curColor = image[sr][sc];
        if(color == curColor)
            return;
        vector<vector<bool>> visited(n,vector<bool>(m,false));
        vector<pair<int,int>> v = {{0,1},{0,-1},{1,0},{-1,0}};
        queue<pair<int,int>> q; 
        q.push({sr,sc});
        while(!q.empty())
        {
            auto [row,col] = q.front();
            q.pop();
            image[row][col] = color;
            for(int i=0;i<4;i++)
            {
                int nrow = row + v[i].first;
                int ncol = col + v[i].second;
                if(nrow<0 || ncol<0 || nrow==n || ncol==m || visited[nrow][ncol] || image[nrow][ncol]!=curColor)
                    continue;
                visited[nrow][ncol] = true;
                q.push({nrow,ncol});
            }
            
        }
    }
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
        bfs(image,sr,sc,color);
        return image;
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
    void dfs(vector<vector<int>> &image,int sr,int sc,int color,int curColor,int n,int m,vector<vector<bool>> &visited,vector<pair<int,int>> &v)
    {
        image[sr][sc] = color;
        for(int i=0;i<4;i++)
        {
            int nrow = sr + v[i].first;
            int ncol = sc + v[i].second;
            if(nrow<0 || ncol<0 || nrow==n || ncol==m || visited[nrow][ncol] || image[nrow][ncol]!=curColor)
                continue;
            visited[nrow][ncol] = true; 
            dfs(image,nrow,ncol,color,curColor,n,m,visited,v); 
        }
    }
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
        int n = image.size();
        int m = image[0].size();
        int curColor = image[sr][sc];
        if(color == curColor)
            return image;
        vector<pair<int,int>> v = {{0,1},{0,-1},{1,0},{-1,0}};
        vector<vector<bool>> visited(n,vector<bool>(m,false));
        dfs(image,sr,sc,color,curColor,n,m,visited,v);
        return image;
    }
};
```