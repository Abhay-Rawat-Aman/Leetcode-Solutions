# 1233. Remove Sub-Folders from the Filesystem

**Difficulty:** Medium  
**Topics:** String, Sorting   
**LeetCode:** https://leetcode.com/problems/remove-sub-folders-from-the-filesystem/description/ 

---

## Solution 1 - String, Sorting

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(nlogn)` |
| Space Complexity | `O(1)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<string> removeSubfolders(vector<string>& folder) {
        vector<string> ans; 
        sort(folder.begin(),folder.end());
        ans.push_back(folder[0]);
        for(int i=1;i<folder.size();i++)
        {
            string lastData = ans[ans.size()-1]+'/';
            string cur = folder[i];
            auto pos = cur.find(lastData);
            if(pos!=0)
                ans.push_back(folder[i]);
        }
        return ans;
    }
};
```