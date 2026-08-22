# 211. Design Add and Search Words Data Structure

**Difficulty:** Medium  
**Topics:** Trie  
**LeetCode:** https://leetcode.com/problems/design-add-and-search-words-data-structure/description/

---

## Solution 1 - Trie

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
struct Node 
{
    Node *links[26];
    bool flag = false;
    bool ContainKey(char ch)
    {
        return (links[ch-'a']!=NULL);
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
    void Insert(string word)
    {
        Node *t = root;
        for(int i=0;word[i];i++)
        {
            if(!t->ContainKey(word[i]))
                t->links[word[i]-'a'] = new Node();
            t=t->links[word[i]-'a'];
        }
        t->flag = true;
    }
    bool Search(string word)
    { 
        Node *t = root; 
        return fullSearch(word,0,t);
    }
    bool fullSearch(string &word, int index,Node *t)
    {
        if(t!=NULL)
        if(index == word.size())
            return t->flag;
        if(word[index]=='.')
        {
            for(int i=0;i<26;i++)
            {
                bool get = false;
                if(t->links[i])
                    get = fullSearch(word,index+1,t->links[i]);
                if(get)
                    return true;
            }
            return false;
        }
        if(t->ContainKey(word[index]))
            return fullSearch(word,index+1,t->links[word[index]-'a']);
        return false;     
    }
};
class WordDictionary {
public:
    Trie *trie;
    WordDictionary() {
        trie = new Trie();
    }
    
    void addWord(string word) {
        trie->Insert(word);
    }
    
    bool search(string word) {
        return trie->Search(word);
    }
};
```