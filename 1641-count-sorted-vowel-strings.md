# 1641. Count Sorted Vowel Strings  

**Difficulty:** Medium  
**Topics:** Combinatrics   
**LeetCode:** https://leetcode.com/problems/count-sorted-vowel-strings/  

---

## Solution 1 - Combinatrics 

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(1)` |
| Space Complexity | `O(1)` |

---

### C++ Code

```cpp
class Solution {
public:
    int countVowelStrings(int n) {
        //combinatric
        return (n+4)*(n+3)*(n+2)*(n+1)/24;
    }
};
```