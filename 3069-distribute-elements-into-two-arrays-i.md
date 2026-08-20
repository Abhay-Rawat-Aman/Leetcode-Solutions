# 3069. Distribute Elements Into Two Arrays I 

**Difficulty:** Easy  
**Topics:** Array   
**LeetCode:**  https://leetcode.com/problems/distribute-elements-into-two-arrays-i/description/  

---

## Solution 1 - Array

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
    vector<int> resultArray(vector<int>& nums) {
        if(nums.size()==1)
            return nums;
        vector<int> arr1,arr2;
        arr1.push_back(nums[0]);
        arr2.push_back(nums[1]);
        for(int i=2;i<nums.size();i++)
        {
            if(arr1[arr1.size()-1]>arr2[arr2.size()-1])
                arr1.push_back(nums[i]);
            else 
                arr2.push_back(nums[i]);
        }
        for(auto &it:arr2)
            arr1.push_back(it);
        return arr1;
    }
};
```