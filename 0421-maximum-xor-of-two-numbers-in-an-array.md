# 421. Maximum XOR of Two Numbers in an Array

**Difficulty:** Medium  
**Topics:** Trie  
**LeetCode:** https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/description/

---

## Solution 1 - Trie

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n*32)` |
| Space Complexity | `--` |

---

### C++ Code

```cpp
struct Node
{
    Node *links[2];
    bool ContainKey(int bit)
    {
        return (links[bit]!=NULL);
    }
    Node* Get(int bit)
    {
        return links[bit];
    }
    void Put(int bit,Node *node)
    {
        links[bit] = node;
    }
};
class Trie
{
    private : 
    Node *root;
    public :
    Trie()
    {
        root = new Node();
    }
    void Insert(int num)
    {
        Node *node = root;
        for(int i=31;i>=0;i--)
        {
            int bit = (num>>i) & 1;
            if(!node->ContainKey(bit))
            {
                node->Put(bit,new Node());
            }
            node = node->Get(bit);
        }        
    }
    int GetMax(int num)
    {
        Node *node =root;
        int ans=0;
        for(int i=31;i>=0;i--)
        {
            int bit = (num>>i) & 1;
            if(node->ContainKey(1-bit))
            {
                node = node->Get(1-bit);
                ans = ans | (1<<i);
            }
            else
            {
                node = node->Get(bit);
            }
        }
        return ans;
    }
};
class Solution {
public:
    int findMaximumXOR(vector<int>& nums) {
        Trie *trie = new Trie();
        for(int i=0;i<nums.size();i++)
            trie->Insert(nums[i]);
        int ans = 0;
        for(int i=0;i<nums.size();i++)
            ans = max(ans,trie->GetMax(nums[i]));
        return ans;
    }
};
```