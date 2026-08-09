# 3532. Path Existence Queries in a Graph I

**Difficulty:** Medium  
**Topics:** Graph, Find-Union   
**LeetCode:** https://leetcode.com/problems/path-existence-queries-in-a-graph-i/description/  

---

## Solution 1 - Graph, Find-Union

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n^2)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<bool> pathExistenceQueries(int n, vector<int>& nums, int maxDiff, vector<vector<int>>& queries) {
        vector<bool> ans;
        vector<int> parent(n,-1);
        for(int i=0;i<nums.size()-1;i++)
        {
            //find the root node of each node
            for(int j=i+1;j<nums.size() && abs(nums[i]-nums[j])<=maxDiff && parent[j]==-1;j++)
            {
                int p = find(parent,i);
                parent[j] = p;
            }
        }
        for(int i=0;i<queries.size();i++)
        {
            int node1 = queries[i][0]<queries[i][1]?queries[i][0]:queries[i][1];
            int node2 = queries[i][0]>queries[i][1]?queries[i][0]:queries[i][1];
            if(node1==node2)
                ans.push_back(true);
            else if(parent[node1]==-1 && parent[node2]==-1)
                ans.push_back(false);
            else if(parent[node1]==-1 && parent[node2] == node1)
                ans.push_back(true);
            else if(parent[node1]==parent[node2])
                ans.push_back(true);
            else
                ans.push_back(false);
        }
        return ans; 
    }
    int find(vector<int> &parent,int node)
    {
        if(parent[node]==-1)
            return node;
        return parent[node];         
    }
};
```

---

## Solution 2 - Graph, component

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
    vector<bool> pathExistenceQueries(int n, vector<int>& nums, int maxDiff, vector<vector<int>>& queries) {
        vector<bool> ans;
        vector<int> component(n,-1);
        int val = 1;
        component[0] = val;
        for(int i=1;i<nums.size();i++)
        {
            if(nums[i]-nums[i-1]>maxDiff)
                val++;
            component[i] = val;
        }
        for(int i=0;i<queries.size();i++)
        {
            int node1 = queries[i][0]<queries[i][1]?queries[i][0]:queries[i][1];
            int node2 = queries[i][0]>queries[i][1]?queries[i][0]:queries[i][1];
            ans.push_back(component[node1] == component[node2]);
        }
        return ans; 
    }
    int find(vector<int> &parent,int node)
    {
        if(parent[node]==-1)
            return node;
        return parent[node];         
    }
};
```