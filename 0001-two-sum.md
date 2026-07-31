# 1. Two Sum

**Difficulty:** Easy  
**Topics:** Array, Hash Table  
**LeetCode:** https://leetcode.com/problems/two-sum/

---

## Solution 1 - Hash Map

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
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> ans;
        map<int, int> d;

        for (int i = 0; i < nums.size(); i++) {
            int t = target - nums[i];

            if (d.find(t) != d.end()) {
                ans.push_back(d[t]);
                ans.push_back(i);
                return ans;
            }

            d[nums[i]] = i;
        }

        return ans;
    }
};
```

---

## Solution 2 - Brute Force

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n²)` |
| Space Complexity | `O(1)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> ans;

        for (int i = 0; i < nums.size(); i++) {
            for (int j = i + 1; j < nums.size(); j++) {
                if (nums[i] + nums[j] == target) {
                    ans.push_back(i);
                    ans.push_back(j);
                    return ans;
                }
            }
        }

        return ans;
    }
};
```