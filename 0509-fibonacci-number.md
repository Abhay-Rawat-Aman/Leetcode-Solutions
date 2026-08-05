# 509. Fibonacci Number

**Difficulty:** Easy  
**Topics:** Array, DP   
**LeetCode:** https://leetcode.com/problems/fibonacci-number/description/

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
    int fib(int n) {
        if(n<=1)
            return n;
        return fib(n-1)+fib(n-2);
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
    int fib(int n) {
        vector<int> dp(n+1,-1);
        return fibMem(n,dp);
    }
    int fibMem(int n, vector<int> &dp)
    {
        if(n<=1)
        {
            dp[n]= n;
            return dp[n];
        }
        if(dp[n]!=-1)
            return dp[n];
        int ans = fibMem(n-1,dp) + fibMem(n-2,dp);
        dp[n] = ans;
        return dp[n];
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
    int fib(int n) {
        if(n<=1)
            return n;
        vector<int> dp(n+1,-1);
        dp[0] = 0;
        dp[1] = 1;
        for(int i=2;i<=n;i++)
            dp[i] = dp[i-1]+dp[i-2];
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
int fib(int n) {
        if(n<=1)
            return n;
        int prev1,prev2,cur;
        prev1 = 0;
        prev2 = 1;
        for(int i=2;i<=n;i++)
        {
            cur = prev1 + prev2;
            prev1 = prev2; 
            prev2 = cur;
        }
        return cur;
    }
```