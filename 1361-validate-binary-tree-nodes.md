# 1361. Validate Binary Tree Nodes

**Difficulty:** Medium  
**Topics:** Tree, DFS, Find-Union   
**LeetCode:** https://leetcode.com/problems/validate-binary-tree-nodes/  

---

## Solution 1 - Tree, DFS, Find-Union

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
    bool validateBinaryTreeNodes(int n, vector<int>& leftChild, vector<int>& rightChild) {
        vector<int> parent(n,-1);
        for(int i=0;i<n;i++)
        {
            if(leftChild[i]!=-1)
            {
                if(parent[leftChild[i]]==-1)
                    parent[leftChild[i]] = i;
                else
                    return false;
            }
            if(rightChild[i]!=-1)
            {
                if(parent[rightChild[i]]==-1)
                    parent[rightChild[i]] = i;
                else
                    return false;
            }
        }
        int count = 0;
        int root = -1;
        for(int i=0;i<n;i++)
        {
            if(parent[i]==-1)
            {
                count++;
                root = i;
            }
            if(count>1)
                return false;
        }
        if(root==-1)
            return false;
        vector<int> visited(n,0);
        count=0;
        DFS(leftChild,rightChild,visited,root);
        for(int i=0;i<n;i++)
            count+=visited[i];
        return count==n;
    }
    void DFS(vector<int> &left,vector<int> &right,vector<int>& visited,int root)
    {
        if(visited[root]==1)
            return;
        visited[root]=1;
        if(left[root]!=-1)
            DFS(left,right,visited,left[root]);
        if(right[root]!=-1)
            DFS(left,right,visited,right[root]);
    }
};
```