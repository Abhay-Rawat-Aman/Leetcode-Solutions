# 655. Print Binary Tree

**Difficulty:** Medium  
**Topics:** Tree, string, Preorder   
**LeetCode:** https://leetcode.com/problems/print-binary-tree/description/

---

## Solution 1 - Tree, string, Preorder

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n)` |
| Space Complexity | `O(logn)` |

---

### C++ Code

```cpp
class Solution {
    private : 
    int findHeight(TreeNode *root)
    {
        if(!root)
            return 0;
        int left = findHeight(root->left);
        int right = findHeight(root->right);
        return max(left,right)+1;
    }
    int PowOf2(int n)
    {
        int ans = 1;
        for(int i=0;i<n;i++)
            ans*=2;
        return ans;
    }
    void PreOrder(TreeNode *root,int height,int row,int col,vector<vector<string>> &ans)
    {
        if(!root)
            return;
        ans[row][col] = to_string(root->val);
        PreOrder(root->left,height,row+1,col-PowOf2(height-row-2),ans);
        PreOrder(root->right,height,row+1,col+PowOf2(height-row-2),ans);
    }
public:
    vector<vector<string>> printTree(TreeNode* root) {
        int ht = findHeight(root);
        cout<<ht;
        int col = PowOf2(ht)-1;
        vector<vector<string>> ans(ht,vector<string>(col,""));
        PreOrder(root,ht,0,(col-1)/2,ans);
        return ans; 
    }
};
```