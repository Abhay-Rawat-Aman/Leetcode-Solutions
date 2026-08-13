# 3775. Reverse Words With Same Vowel Count  

**Difficulty:** Medium  
**Topics:** String   
**LeetCode:** https://leetcode.com/problems/reverse-words-with-same-vowel-count/description/  

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
    string reverseWords(string s) {
        bool FirstWord = false;
        string word;
        int count=0;
        int firstWordCount;
        string ans;
        s.push_back(' ');
        for(int i=0;s[i];i++)
        {
            if(s[i]==' ')
            {
                if(FirstWord==false)
                {
                    FirstWord = true;
                    firstWordCount = count;
                }
                else
                {
                    if(firstWordCount == count)
                        word = Reverse(word);
                    ans.push_back(' ');
                }
                ans += word;
                word = "";
                count=0;
            }
            else
            {
                if(CheckVowel(s[i]))
                    count++;
                word.push_back(s[i]);
            }
        }
        return ans;
    }
    string Reverse(string word)
    {
        int n = word.size();
        for(int i=0;i<n/2;i++)
        {
            int temp = word[i];
            word[i] = word[n-i-1];
            word[n-1-i] = temp;
        }
        return word;
    }
    bool CheckVowel(char ch)
    {
        switch(ch)
        {
            case 'a':
            case 'e':
            case 'i':
            case 'o':
            case 'u':   return true;
            default: return false;
        }
    }
};
```