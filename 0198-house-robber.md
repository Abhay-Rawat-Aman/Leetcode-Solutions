# 198. House Robber

**Difficulty:** Easy  
**Topics:** Array, DP, Recursion  
**LeetCode:** https://leetcode.com/problems/house-robber/

---

## Solution 1 - Recusion

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(2^n)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Solution {
public:
    int robRec(vector<int> &nums, int index)
    {
        if(index < 0)
            return 0;
        int take = nums[index] + robRec(nums,index-2);
        int notTake = 0 + robRec(nums,index-1);
        return max(take,notTake);
    }
    int rob(vector<int>& nums) {
        int ans; 
        ans = robRec(nums,nums.size()-1);
        return ans;
    }
};
```

---

## Solution 2 - DP Memorization

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
    int robMem(vector<int> &nums, int index,vector<int> &dp)
    {
        if(index < 0)
            return 0;
        if(dp[index]!=-1)
            return dp[index];
        int take = nums[index] + robMem(nums,index-2,dp);
        int notTake = 0 + robMem(nums,index-1,dp);
        dp[index] = max(take,notTake);
        return dp[index];
    }
    int rob(vector<int>& nums) {
        int ans;
        int n = nums.size();
        vector<int> dp(n+1,-1);
        ans = robMem(nums,n-1,dp);
        return ans;
    }
};
```

---

## Solution 3 - DP Tabulation

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
    int rob(vector<int>& nums) {
        return robTab(nums);
    }
    int robTab(vector<int> &nums)
    {
        int n = nums.size();
        vector<int> dp(n,-1);
        dp[0] = nums[0];
        for(int i=1;i<n;i++)
        {
            int take = nums[i];
            if(i>1)
                take += dp[i-2];
            int nottake = 0 + dp[i-1];
            dp[i] = max(take,nottake);
        }
        return dp[n-1];
    }
};
```

---

## Solution 4 - DP Tabulation with space optimization  

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
    int rob(vector<int>& nums) {
        return robTabWithOpt(nums);
    }
    int robTabWithOpt(vector<int> &nums)
    {
        int n = nums.size();
        int cur = 0, prev = 0, prev2 = nums[0];
        for(int i=1;i<n;i++)
        {
            int take = nums[i] + prev;
            int nottake = 0 + prev2;
            cur = max(take,nottake);
            prev = prev2; 
            prev2 = cur;
        }
        return prev2;
    }
};
```