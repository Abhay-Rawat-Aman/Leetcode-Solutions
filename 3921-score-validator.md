# 3921. Score Validator  

**Difficulty:** Easy  
**Topics:** Array, String   
**LeetCode:** https://leetcode.com/problems/score-validator/description/ 

---

## Solution 1 - String

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n)` |
| Space Complexity | `O(1)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<int> scoreValidator(vector<string>& events) {
        vector<int> ans; 
        int score = 0;
        int counter = 0;
        for(int i=0;i<events.size();i++)
        {
            string event = events[i];
            if(event.size()==2)
                score++;
            else if(event[0]>='0' && event[0]<='6')
                score = score + event[0]-'0';
            else
                counter++;
            if(counter==10)
                break;
        }
        ans.push_back(score);
        ans.push_back(counter);
        return ans;
    }
};
```