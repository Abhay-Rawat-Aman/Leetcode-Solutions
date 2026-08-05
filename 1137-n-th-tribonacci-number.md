# 1137. N-th Tribonacci Number

**Difficulty:** Easy  
**Topics:** Array, DP   
**LeetCode:** https://leetcode.com/problems/n-th-tribonacci-number/description/

---

## Solution 1 - Recursion

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(3^n)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Solution {
public:
    int tribonacci(int n) {
        if(n==0)
            return 0;
        if(n==1 || n==2)
            return 1;
        return tribonacci(n-1) + tribonacci(n-2) + tribonacci(n-3);
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
    int tribonacciMem(int n,vector<int> &dp) 
    {
        if(n==0)
        {
            dp[n] = 0;
            return dp[n];
        }
        if(n==1 || n==2)
        {
            dp[n] = 1;
            return dp[n];
        }
        
        if(dp[n]!=-1)
            return dp[n];

        int ans = tribonacciMem(n-1,dp) + tribonacciMem(n-2,dp) + tribonacciMem(n-3,dp);
        dp[n] = ans;
        return dp[n];
    }
    int tribonacci(int n) {
        vector<int> dp(n+1,-1);
        return tribonacciMem(n,dp);
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
    int tribonacci(int n) {
        return tribonacciTab(n);
    }
    int tribonacciTab(int n)
    {
        if(n==0)
            return 0;
        if(n==1 || n==2)
            return 1;
        vector<int> dp(n+1,-1);
        dp[0] = 0;
        dp[1] = dp[2] = 1;
        for(int i=3;i<=n;i++)
            dp[i] = dp[i-1] + dp[i-2] + dp[i-3];
        return dp[n];
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
    int tribonacci(int n) {
        return tribonacciTabWithSpaceOpt(n);
    }
    int tribonacciTabWithSpaceOpt(int n)
    {
        if(n==0)
            return 0;
        if(n==1 || n==2)
            return 1;
        int prev,prev1,prev2,ans;
        prev = prev1 = 1;
        prev2 = 0;
        for(int i=3;i<=n;i++)
        {
            ans = prev + prev1 + prev2; 
            prev2 = prev1; 
            prev1 = prev; 
            prev = ans;
        }
        return ans;
    }
};
```