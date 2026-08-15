# 3885. Design Event Manager  

**Difficulty:** Medium  
**Topics:** Map, Set  
**LeetCode:** https://leetcode.com/problems/design-event-manager/description/ 

---

## Solution 1 - Map Set

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(nlogn)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class EventManager {
public:
    unordered_map<int,int> m;
    set<pair<int,int>> s;
    EventManager(vector<vector<int>>& events) {
        for(auto &event:events)
        {
            m[event[0]] = event[1];
            s.insert({event[1],-event[0]});
        }
    }
    
    void updatePriority(int eventId, int newPriority) {
       int oldPriority = m[eventId];
       s.erase({oldPriority,-eventId});
       m[eventId] = newPriority;
       s.insert({newPriority,-eventId});
    }
    
    int pollHighest() {
        if(s.size()==0)
            return -1;
        auto it = s.rbegin();
        auto [p,e] = *it;
        s.erase({p,e});
        return -e;
    }
};
```