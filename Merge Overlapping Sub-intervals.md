## Merge Overlapping Sub-intervals (c++)

Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

## Example
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]

Output: [[1,6],[8,10],[15,18]]

Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {

        sort(intervals.begin(),intervals.end());
        int n=intervals.size();
        vector<vector<int>>ans;

        for(int i=0;i<n;i++)
        {
            if(ans.empty() || ans.back()[1] < intervals[i][0])
            {
                ans.push_back(intervals[i]);
            }
            else
            {
                ans.back()[1]=max(ans.back()[1],intervals[i][1]);
            }
        }
        return ans;
    }
};
```
## Complexity
- Time complexity : O(N + N logN)

- Space complexity : O(1) 
