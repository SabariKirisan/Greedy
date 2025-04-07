## Jump Game (c++)

You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.

## Example
Input: nums = [2,3,1,1,4]

Output: true

Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    bool canJump(vector<int>& nums) 
    {
        int n=nums.size();
        int maxx=0;

        for(int i=0;i<n;i++)
        {
            if(i>maxx) return false;

            maxx=max(maxx,(i+nums[i]));
        }
        return true;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(1)
