## Valid Parenthesis String  (c++)

Given a string s containing only three types of characters: '(', ')' and '*', return true if s is valid.

The following rules define a valid string:

Any left parenthesis '(' must have a corresponding right parenthesis ')'.

Any right parenthesis ')' must have a corresponding left parenthesis '('.

Left parenthesis '(' must go before the corresponding right parenthesis ')'.

'*' could be treated as a single right parenthesis ')' or a single left parenthesis '(' or an empty string "".
## Example
Input: s = "()"

Output: true
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    bool checkValidString(string s) 
    {
        int n=s.size();

        int maxx=0,minn=0;

        for(int i=0;i<n;i++)
        {
            if('('==s[i])
            {
                maxx++;
                minn++;
            }
            else if(')'==s[i])
            {
                maxx--;
                minn--;
            }
            else
            {
                minn--;
                maxx++;
            }
            if(minn < 0) minn=0;
            if(maxx < 0) return false;
        }
        if(minn==0) return true;
        return false;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(1) 
