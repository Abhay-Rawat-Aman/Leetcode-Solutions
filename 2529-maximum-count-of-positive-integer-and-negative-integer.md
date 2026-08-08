# 2529. Maximum Count of Positive Integer and Negative Integer

**Difficulty:** Easy  
**Topics:** Array   
**LeetCode:** https://leetcode.com/problems/maximum-count-of-positive-integer-and-negative-integer/description/   

---

## Solution 1 - Linear Search

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
    int maximumCount(vector<int>& nums) {
        int neg=0,zero=0; 
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]<0)
                neg++;
            else if(nums[i]==0)
                zero++;
            else
                break;
        }
        int pos = nums.size()-neg-zero;
        return (pos>neg?pos:neg);
    }
};
```

---

## Solution 2 - Binary Search

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
    int minNegativeNo(vector<int> &nums)
    {
        int beg = 0;
        int end = nums.size()-1;
        int index = -1;
        while(beg<=end)
        {
            int mid = (beg+end)/2;
            if(nums[mid]<0)
            {
                beg = mid+1;
                index = mid;
            }
            else
                end = end-1;
        }
        cout<<index<<" ";
        return index;
    }
    int minPostiveNo(vector<int> &nums)
    {
        int beg = 0;
        int end = nums.size()-1;
        int index = end+1;
        while(beg<=end)
        {
            int mid = (beg+end)/2;
            if(nums[mid]>0)
            {
                end = mid-1;
                index = mid;
            }
            else 
                beg = mid+1;
        }
        cout<<index<<endl;
        return index;
    }
    int maximumCount(vector<int>& nums) {
        int neg = minNegativeNo(nums)+1;
        int pos = nums.size()-minPostiveNo(nums);
        return neg>pos?neg:pos;
    }
};
```