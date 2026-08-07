# 3606. Coupon Code Validator

**Difficulty:** Easy  
**Topics:** String   
**LeetCode:** https://leetcode.com/problems/coupon-code-validator/description/ 

---

## Solution 1 - String

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(nlogn)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Solution {
public:
    vector<string> validateCoupons(vector<string>& code, vector<string>& businessLine, vector<bool>& isActive) {
        vector<string> ans; 
        vector<string> v[4]; 
        int n = code.size();
        for(int i=0;i<n;i++)
        {
            string cpnCd = code[i];
            if(isActive[i]==false || cpnCd.size()==0)
                continue;
            cout<<cpnCd<<" ";
            bool consider = true;
            for(int j=0;cpnCd[j];j++)
            {
                if(cpnCd[j]>='a' && cpnCd[j]<='z')
                {}
                else if(cpnCd[j]>='A' && cpnCd[j]<='Z')
                {}
                else if(cpnCd[j]>='0' && cpnCd[j]<='9')
                {}
                else if(cpnCd[j]=='_')
                {}
                else
                {
                    consider = false;
                    break;
                }
            }
            int index = -1;
            if(businessLine[i]=="electronics")
                index = 0;
            else if(businessLine[i]=="grocery")
                index = 1;
            else if(businessLine[i]=="pharmacy")
                index = 2;
            else if(businessLine[i]=="restaurant")
                index = 3;
            if(consider && index!=-1)
                v[index].push_back(cpnCd);
        }
        for(int i=0;i<4;i++)
        {
            sort(v[i].begin(),v[i].end());
            for(auto &it:v[i])
                ans.push_back(it);
        }
        return ans;
    }
};
```