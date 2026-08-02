# 3898. Find the Degree of Each Vertex

**Difficulty:** Easy  
**Topics:** Graph  
**LeetCode:** https://leetcode.com/problems/find-the-degree-of-each-vertex/description/  

---

## Solution - Graph 

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n2)` |
| Space Complexity | `O(1)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<int> findDegrees(vector<vector<int>>& matrix) {
        vector<int> ans;
        for(int i=0;i<matrix.size();i++)
        {
            int sum = 0;
            for(int j=0;j<matrix.size();j++)
                sum+=matrix[i][j];
            ans.push_back(sum);
        }
        return ans;
    }
};
```