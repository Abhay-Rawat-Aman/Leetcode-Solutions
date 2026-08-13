# 105. Construct Binary Tree from Preorder and Inorder Traversal  

**Difficulty:** Medium  
**Topics:** Tree, Divide and Conquere   
**LeetCode:** https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description  

---

## Solution 1 - Tree, Divide and Conquere

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
    TreeNode* Rec(int &index,int start,int end,vector<int> &preorder,unordered_map<int,int> &inorder)
    {
        cout<<index<<" "<<start<<" "<<end<<endl;
        if( index>preorder.size() || start>end)
            return NULL;
        TreeNode *node = new TreeNode(preorder[index++]);
        int actualIndex = inorder[node->val];
        
        node->left = Rec(index,start,actualIndex-1,preorder,inorder);
        node->right = Rec(index,actualIndex+1,end,preorder,inorder);
        return node;
    }
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        TreeNode *root; 
        unordered_map<int,int> m; 
        for(int i=0;i<inorder.size();i++)
            m[inorder[i]] = i; 
        int index=0;
        root = Rec(index,0,preorder.size()-1,preorder,m);
        return root;
    }
};
```