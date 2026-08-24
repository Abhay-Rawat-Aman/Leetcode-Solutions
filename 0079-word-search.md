# 79. Word Search

**Difficulty:** Medium  
**Topics:** Backtracking, DFS  
**LeetCode:** https://leetcode.com/problems/word-search/description/

---

## Solution 1 - Backtracking, DFS

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n*m*3^(word.size))` |
| Space Complexity | `O(n*m)` |

---

### C++ Code

```cpp
class Solution {
public:
    bool dfs(int index,int row,int col,vector<vector<char>> &board,string word,vector<vector<bool>> &visited,vector<pair<int,int>> &v,int n,int m)
    {
        visited[row][col]=true;
        if(word.size()==index)
            return true;
        for(int i=0;i<4;i++)
        {
            int nrow = row+v[i].first;
            int ncol = col+v[i].second;
            if(nrow<0 || ncol<0 || nrow==n || ncol==m || visited[nrow][ncol] || board[nrow][ncol]!=word[index])
                continue;
            if(dfs(index+1,nrow,ncol,board,word,visited,v,n,m))
                return true;
        }
        visited[row][col]=false;
        return false;
    }
    bool exist(vector<vector<char>>& board, string word) {
        int n = board.size();
        int m = board[0].size();
        vector<pair<int,int>> v = {{0,1},{0,-1},{1,0},{-1,0}};
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                vector<vector<bool>> visited(n,vector<bool>(m,false));
                if(board[i][j]==word[0] && dfs(1,i,j,board,word,visited,v,n,m))
                    return true;
            }
        }
        return false;
    }
};
```