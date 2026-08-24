# 81. Search in Rotated Sorted Array II

**Difficulty:** Medium  
**Topics:** Array, Binary Search  
**LeetCode:** https://leetcode.com/problems/search-in-rotated-sorted-array-ii/description/

---

## Solution 1 - Array, Binary Search

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
    bool search(vector<int>& nums, int target) {
        int i = 0;
        int j = nums.size()-1;
        while(i<=j)
        {
            int mid = i-(i-j)/2;
            if(nums[mid]==target)
                return true;
            if(nums[i]<nums[mid] || nums[mid]>nums[j])
            {
                //left side is assending order
                if(target>=nums[i] && target<nums[mid])
                    j = mid-1;
                else
                    i = mid+1;
            }
            else if(nums[mid]<nums[j] || nums[i]>nums[mid])
            {
                //right side is assending order
                if(target>nums[mid] && target<=nums[j])
                    i = mid+1;
                else
                    j = mid-1;
            }
            else
            {
                i++;
                j--;
            }
        }
        return false;
    }
};
```

---

## Solution 2 - Array, Binary Search

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
    bool search(vector<int>& nums, int target) {
        int i = 0;
        int j = nums.size()-1;
        while(i<=j)
        {
            int mid = i-(i-j)/2;
            if(nums[mid]==target)
                return true;
            //with dublicate we can have this condtion, just update
            else if(nums[i]==nums[mid] && nums[j]==nums[mid])
            {
                i++;
                j--;
            }
            //first half
            //first half is in order 
            else if(nums[i]<=nums[mid])
            {
                //target is in first half
                if(target>=nums[i] && target<nums[mid])
                    j = mid-1;
                else
                    i = mid+1;
            }
            //second half
            //second half in order
            // target is in second half
            else
            {
                if(target>nums[mid] && target<=nums[j])
                    i = mid+1;
                else
                    j = mid-1;
            }
        }
        return false;
    }
};
```