## Insert Interval  (c++)

You are given an array of non-overlapping intervals intervals where intervals[i] = [starti, endi] represent the start and the end of the ith interval and intervals is sorted in ascending order by starti. You are also given an interval newInterval = [start, end] that represents the start and end of another interval.

Insert newInterval into intervals such that intervals is still sorted in ascending order by starti and intervals still does not have any overlapping intervals (merge overlapping intervals if necessary).

Return intervals after the insertion.

Note that you don't need to modify intervals in-place. You can make a new array and return it.

## Example
Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]

Output: [[1,2],[3,10],[12,16]]

Explanation: Because the new interval [4,8] overlaps with [3,5],[6,7],[8,10].
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    vector<vector<int>> insert(vector<vector<int>>& intervals, vector<int>& newInterval) 
    {
        int n=intervals.size();
        vector<vector<int>>res;
        int i=0;

        while(i<n && intervals[i][1]<newInterval[0])
        {
            res.push_back(intervals[i]);
            i++;
        }
        while(i<n && intervals[i][0]<=newInterval[1])
        {
            newInterval[0]=min(intervals[i][0],newInterval[0]);
            newInterval[1]=max(intervals[i][1],newInterval[1]);
            i++;       
        }
        res.push_back(newInterval);

        while(i<n)
        {
            res.push_back(intervals[i]);
            i++;
        }
        return res;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N) 
