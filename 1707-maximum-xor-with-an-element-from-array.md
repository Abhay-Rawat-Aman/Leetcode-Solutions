# 1707. Maximum XOR With an Element From Array

**Difficulty:** Hard  
**Topics:** Trie  
**LeetCode:** https://leetcode.com/problems/maximum-xor-with-an-element-from-array/description/

---

## Solution 1 - Trie

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(N log N + Q log Q)` |
| Space Complexity | `O(N+Q)` |

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
    Node* GetNode(int bit)
    {
        return links[bit];
    }
    void PutNode(int bit,Node *node)
    {
        links[bit] = node;
    }
};
class Trie
{
    private : 
    Node *root;
    public:
    Trie()
    {
        root = new Node();
    }
    void Insert(int nums)
    {
        Node *t = root;
        for(int i = 31;i>=0;i--)
        {
            int bit = (nums>>i)&1;
            if(!t->ContainKey(bit))
                t->PutNode(bit,new Node());
            t = t->GetNode(bit);
        }
    }
    int GetMax(int nums)
    {
        Node *t = root; 
        int ans = 0;
        for(int i=31;i>=0;i--)
        {
            int bit = (nums>>i)&1;
            if(t->ContainKey(1-bit))
            {
                t = t->GetNode(1-bit);
                ans = ans | (1<<i);
            }
            else 
                t = t->GetNode(bit);
        }
        return ans;
    } 
};
class Solution {
public:
    vector<int> maximizeXor(vector<int>& nums, vector<vector<int>>& queries) {
        int n = queries.size();
        vector<int> ans(n);
        sort(nums.begin(),nums.end());
        vector<tuple<int,int,int>> newQuery;
        for(int i=0;i<queries.size();i++)
            newQuery.push_back({queries[i][1],queries[i][0],i});
        sort(newQuery.begin(),newQuery.end());
        Trie *trie = new Trie();
        int numsIndex = 0; 
        for(auto &it:newQuery)
        {
            auto [mi,xi,index] = it;
            while(numsIndex<nums.size() && nums[numsIndex]<=mi)
            {
                trie->Insert(nums[numsIndex]);
                numsIndex++;
            }
            ans[index] = numsIndex==0?-1:trie->GetMax(xi); 
        }
        return ans;
    }
};
```