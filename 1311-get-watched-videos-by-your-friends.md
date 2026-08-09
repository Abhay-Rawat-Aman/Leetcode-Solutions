# 1311. Get Watched Videos by Your Friends

**Difficulty:** Medium  
**Topics:** Graph, Sorting, BFS, Counting   
**LeetCode:** https://leetcode.com/problems/get-watched-videos-by-your-friends/  

---

## Solution 1 - Graph, BFS, Sorting

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
    vector<string> watchedVideosByFriends(vector<vector<string>>& watchedVideos, vector<vector<int>>& friends, int id, int level) {
        int n = friends.size();
        vector<bool> visited(n,false);
        unordered_map<string,int> m;
        queue<pair<int,int>> q;
        q.push({id,0});
        visited[id] = true;
        while(!q.empty())
        {
            auto node = q.front();
            cout<<node.first<<" "<<node.second<<endl;
            if(node.second>level)
                break;
            else if(node.second == level)
            {
                for(auto &it:watchedVideos[node.first])
                    m[it]++;
            }
            for(auto &it:friends[node.first])
            {
                if(visited[it]==false)
                {
                    visited[it] = true; 
                    q.push({it,node.second+1});
                }
            }
            q.pop();
        }
        vector<pair<int,string>> v; 
        vector<string> ans; 
        for(auto &it:m)
            v.push_back({it.second,it.first});
        sort(v.begin(),v.end());
        for(int i=0;i<v.size();i++)
            ans.push_back(v[i].second);
        return ans; 
    }
};
```

---

## Solution 2 - Graph, BFS, Priority Queue

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
    vector<string> watchedVideosByFriends(vector<vector<string>>& watchedVideos, vector<vector<int>>& friends, int id, int level) {
        int n = friends.size();
        vector<bool> visited(n,false);
        unordered_map<string,int> m;
        queue<pair<int,int>> q;
        q.push({id,0});
        visited[id] = true;
        while(!q.empty())
        {
            auto node = q.front();
            cout<<node.first<<" "<<node.second<<endl;
            if(node.second>level)
                break;
            else if(node.second == level)
            {
                for(auto &it:watchedVideos[node.first])
                    m[it]++;
            }
            for(auto &it:friends[node.first])
            {
                if(visited[it]==false)
                {
                    visited[it] = true; 
                    q.push({it,node.second+1});
                }
            }
            q.pop();
        }
        priority_queue<pair<int,string>,
                      vector<pair<int,string>>,
                      greater<pair<int,string>>> pq;
        for(auto &it:m)
            pq.push({it.second,it.first});
        vector<string> ans; 
        while(!pq.empty())
        {
            auto t = pq.top();
            ans.push_back(t.second);
            pq.pop();
        }
        return ans; 
    }
};
```