# 889. Construct Binary Tree from Preorder and Postorder Traversal

**Difficulty:** Medium  
**Topics:** Array, Divide and conqure  
**LeetCode:** https://leetcode.com/problems/construct-binary-tree-from-preorder-and-postorder-traversal/description/

---

## Solution - Divide and conqure 

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
    TreeNode* CreateTree(vector<int>& preorder,int start, int end,int &index,unordered_map<int,int>& m,vector<int> &postorder)
    {
        TreeNode *ptr = new TreeNode(postorder[end]);
        if(start==end)
            return ptr;
        if(index>=postorder.size())
            return NULL;
        if(start>end)
        {
            index--;
            return NULL; 
        }
        
        int pos = m[preorder[index]];
        index++;
        ptr->left = CreateTree(preorder,start,pos,index,m,postorder);
        index++;
        ptr->right = CreateTree(preorder,pos+1,end-1,index,m,postorder);

        return ptr;

    }
    TreeNode* constructFromPrePost(vector<int>& preorder, vector<int>& postorder) {
        TreeNode *root;
        unordered_map<int,int> m;
        int n = postorder.size();
        for(int i=0;i<n;i++)
            m[postorder[i]] = i;
        int index = 1;
        root = CreateTree(preorder,0,n-1,index,m,postorder);
        return root; 
    }
};
```