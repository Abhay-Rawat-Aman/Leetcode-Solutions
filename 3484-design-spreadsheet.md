# 3484. Design Spreadsheet

**Difficulty:** Medium  
**Topics:** Array, Map   
**LeetCode:** https://leetcode.com/problems/design-spreadsheet/description/ 

---

## Solution 1 - Array and Map

### Complexity Analysis

| Metric | Complexity |
|--------|------------|
| Time Complexity | `O(n)` |
| Space Complexity | `O(n)` |

---

### C++ Code

```cpp
class Spreadsheet {
public:
    unordered_map<string,int> m;
    Spreadsheet(int rows) {
        
    }
    
    void setCell(string cell, int value) {
        m[cell] = value;
    }
    
    void resetCell(string cell) {
        m.erase(cell);
    }
    
    int getValue(string formula) {
        int ans;
        string first,second;
        bool plus = false;
        int num1 = 0,num2 = 0;
        for(int i=1;i<formula.size();i++)
        {
            if(formula[i]=='+')
                plus = true;
            else if(plus)
                second.push_back(formula[i]);
            else
                first.push_back(formula[i]);
        }
        if(first[0]>='A' && first[0]<='Z')
            num1 = m[first];
        else
            num1 = stoi(first);
        if(second[0]>='A' && first[0]<='Z')
            num2 = m[second];
        else
            num2 = stoi(second);
        return num1+num2;
    }
};
```