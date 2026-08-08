# 3941. Password Strength  

**Difficulty:** Medium  
**Topics:** Array, String   
**LeetCode:** https://leetcode.com/problems/password-strength/description/ 

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
    int passwordStrength(string password) {
        int n; 
        vector<int> small(26,0);
        vector<int> large(26,0);
        vector<int> num(10,0);
        vector<int> special(4,0);
        for(int i=0;password[i];i++)
        {
            if(password[i]>='A' && password[i]<='Z')
                large[password[i]-'A']=1;
            else if(password[i]>='a' && password[i]<='z')
                small[password[i]-'a']=1;
            else if(password[i]>='0' && password[i]<='9')
                num[password[i]-'0'] = 1;
            else if(password[i]=='!')
                special[0] = 1;
            else if(password[i]=='@')
                special[1] = 1;
            else if(password[i]=='#')
                special[2] = 1;
            else if(password[i]=='$')
                special[3] = 1;
        }
        int sm = Count(small);
        int lg = Count(large);
        int sp = Count(special);
        int di = Count(num);
        return sm + lg*2 + 3*di + 5*sp;
    }
    int Count(vector<int> arr)
    {
        int c = 0;
        for(int i=0;i<arr.size();i++)
            c+=arr[i];    
        return c;
    }
};
```