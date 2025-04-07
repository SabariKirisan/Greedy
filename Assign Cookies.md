## Assign Cookies (c++)

Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie.

Each child i has a greed factor g[i], which is the minimum size of a cookie that the child will be content with; and each cookie j has a size s[j]. If s[j] >= g[i], we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximize the number of your content children and output the maximum number.

## Example
Input: g = [1,2], s = [1,2,3]

Output: 2

Explanation: You have 2 children and 3 cookies. The greed factors of 2 children are 1, 2. 
You have 3 cookies and their sizes are big enough to gratify all of the children, 
You need to output 2.
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) 
    {
        int n=g.size();
        int m=s.size();
        int l=0,r=0;
        sort(g.begin(),g.end());
        sort(s.begin(),s.end());

        while(l<m && r<n)
        {
            if(s[l]>=g[r])
            {
                r++;
            }
            l++;
        }
        return r;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(1)
