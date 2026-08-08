# 3913. Sort Vowels by Frequency

**Difficulty:** Medium  
**Topics:** String, Counting  
**LeetCode:** https://leetcode.com/problems/sort-vowels-by-frequency/description/  

---

## Solution - String, Counting 

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
    string sortVowels(string s) {
        string ans;
        vector<int> vowel(5,0);
        vector<int> vowelPos(5,-1);
        for(int i=0;s[i];i++)
        {
            int v = isVowel(s[i]);
            if(v!=-1)
            {
                vowel[v]++;
                if(vowelPos[v]==-1)
                    vowelPos[v] = i;
            }
        }
        int pos = CalMax(vowel,vowelPos);
        for(int i=0;s[i];i++)
        {
            if(isVowel(s[i])==-1)
                ans.push_back(s[i]);
            else
            {
                if(vowel[pos]!=0)
                {
                    ans.push_back(VowelData(pos));
                    vowel[pos]--;
                    if(vowel[pos]==0)
                        pos = CalMax(vowel,vowelPos);
                }
            }
        }
        return ans;
    }
    int CalMax(vector<int> &vowel, vector<int> &vowelPos)
    {
        int mx = INT_MIN;
        int pos = INT_MAX;
        int index;
        for(int i=0;i<5;i++)
        {
            if(vowel[i]>mx && vowel[i]>0)
            {
                mx = vowel[i];
                pos = vowelPos[i];
                index = i;
            }
            else if(mx==vowel[i] && pos>vowelPos[i])
            {
                pos = vowelPos[i];
                index = i;
            }
        }
        return index;
    }
    int isVowel(char ch)
    {
        switch(ch)
        {
            case 'a': return 0;
            case 'e': return 1;
            case 'i': return 2;
            case 'o': return 3;
            case 'u': return 4;
            default : return -1;
        }
        return -1;
    }
    char VowelData(int pos)
    {
        switch(pos)
        {
            case 0: return 'a';
            case 1: return 'e';
            case 2: return 'i';
            case 3: return 'o';
            case 4: return 'u';
        }
        return '1';
    }
};
```