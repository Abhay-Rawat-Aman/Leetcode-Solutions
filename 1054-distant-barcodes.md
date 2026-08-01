# 1054. Distant Barcodes

**Difficulty:** Medium  
**Topics:** Array, Map, Priority Queue  
**LeetCode:** https://leetcode.com/problems/distant-barcodes/description/  

---

## Solution 1 - Map and Priority Queue

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(nlogn)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<int> rearrangeBarcodes(vector<int>& barcodes) {
        int n = barcodes.size();
        if(n==0 || n==1)
            return barcodes; 
        vector<int> ans(n,0);
        unordered_map<int,int> m; 
        for(int i=0;i<n;i++)
            m[barcodes[i]]++;
        priority_queue<pair<int,int>> pq;
        for(auto &it:m)
            pq.push({it.second,it.first});
        int index = 0;
        int change = 0;
        while(!pq.empty())
        {
            auto val = pq.top();
            pq.pop();
            while(val.first--)
            {
                if(index >= n)
                    index = 1;
                ans[index] = val.second;
                index+=2;

            }

        }
        return ans;
    }
};
```

---

## Solution 2 - Map

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
    vector<int> rearrangeBarcodes(vector<int>& barcodes) {
        int n = barcodes.size();
        if(n==0 || n==1)
            return barcodes; 
        vector<int> ans(n,0);
        unordered_map<int,int> m; 
        int mx = 1,act = barcodes[0];
        for(int i=0;i<n;i++)
        {
            m[barcodes[i]]++;
            if(mx<m[barcodes[i]])
            {
                mx = m[barcodes[i]];
                act = barcodes[i];
            }
        }
        int index = 0;
        m.erase(act);
        while(mx--)
        {
            ans[index] = act;
            index+=2;
        }
        for(auto &it:m)
        {
            while(it.second--)
            {    
                if(index>=n)
                    index=1;
                ans[index] = it.first;
                index+=2;
            }
        }
        return ans;
    }
};
```