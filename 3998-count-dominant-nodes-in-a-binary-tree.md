# 3998. Count Dominant Nodes in a Binary Tree 

**Difficulty:** Medium  
**Topics:** Tree   
**LeetCode:**  https://leetcode.com/problems/count-dominant-nodes-in-a-binary-tree/description/  

---

## Solution 1 - Tree

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
    int Rec(int &count,TreeNode *root)
    {
        if(!root)
            return INT_MIN;
        int left = Rec(count,root->left);
        int right = Rec(count,root->right);
        if(left<=root->val && right<=root->val)
        {
            count++;
            return root->val;
        }
        return max(left,right);
    }
    int countDominantNodes(TreeNode* root) {
        int ans; 
        int count=0;
        ans = Rec(count,root);
        return count;
    }
};
```