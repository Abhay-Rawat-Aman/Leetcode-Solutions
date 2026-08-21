# 208. Implement Trie (Prefix Tree)

**Difficulty:** Medium  
**Topics:** Trie  
**LeetCode:** https://leetcode.com/problems/implement-trie-prefix-tree/description/

---

## Solution 1 - Trie Implementation

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Trie {
public:
    struct Node 
    {
        Node *links[26];
        bool flag = false;
    };
    Node *root;
    Trie() {
        root = new Node();
    }
    
    void insert(string word) {
        Node *t = root;
        for(int i=0;word[i];i++)
        {
            char ch=word[i]-'a';
            if(!t->links[ch])
            {
                Node *n = new Node();
                t->links[ch] = n;
            }
            t = t->links[ch];
        }
        t->flag = true;
    }
    
    bool search(string word) {
        Node *t = root;
        for(int i=0;word[i];i++)
        {
            char ch = word[i]-'a';
            if(t->links[ch])
                t=t->links[ch];
            else
                return false;
        }
        return t->flag;
    }
    
    bool startsWith(string prefix) {
        Node *t = root;
        for(int i=0;prefix[i];i++)
        {
            char ch = prefix[i]-'a';
            if(t->links[ch])
                t=t->links[ch];
            else
                return false;
        }
        return true;
    }
};
```