# 1104. Path In Zigzag Labelled Binary Tree

**Difficulty:** Medium  
**Topics:** Array, Maths  
**LeetCode:** https://leetcode.com/problems/path-in-zigzag-labelled-binary-tree/description/  

---

## Solution - Maths 

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(logn)` |
| Space Complexity | `O(1)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<int> pathInZigZagTree(int label) {
        int level = log2(label);
        vector<int> ans(level+1,0);
        ans[level] = label;
        int pos; 
        if(level%2!=0)
        {
            int firstVal = (1<<(level+1))-1;   
            pos = abs(firstVal - label) + 1; 
        }
        else
        {
            int firstVal = (1<<level);
            pos = abs(label - firstVal) + 1;
        }
        cout<<pos<<" ";
        // pos = 27;
        for(int i=level-1;i>=0;i--)
        {
             if(pos%2==0)
                pos=pos/2;
            else
                pos = (pos+1)/2;
            if(i%2!=0)
            {
                int firstVal = (1<<(i+1))-1;
                ans[i] = firstVal - pos + 1;
            }
            else
            {
                int firstVal = (1<<i);
                ans[i] = firstVal + pos - 1;
            }
        }
        return ans;
    }
};
```