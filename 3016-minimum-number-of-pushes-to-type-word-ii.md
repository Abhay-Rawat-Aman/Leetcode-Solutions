# 3016. Minimum Number of Pushes to Type Word II

**Difficulty:** Medium  
**Topics:** Array, Priority Queue  
**LeetCode:** https://leetcode.com/problems/minimum-number-of-pushes-to-type-word-ii/description/

---

## Solution - Priority Queue

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
    int minimumPushes(string word) {
        vector<int> a(26,0);
        for(int i=0;word[i];i++)
            a[word[i]-'a']++;
        priority_queue<int> q; 
        for(int i=0;i<26;i++)
        {
            if(a[i]!=0)
                q.push(a[i]);
        }
        int ans = 0;
        int element = 2, level = 1; 
        while(!q.empty())
        {
            int freq = q.top();
            ans = ans + freq*level;
            element++;
            if(element>9)
            {
                level++;
                element = 2;
            }
            q.pop();
        }
        return ans;
    }
};
```

