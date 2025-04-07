## N meetings in one room (c++)

You are given timings of n meetings in the form of (start[i], end[i]) where start[i] is the start time of meeting i and end[i] is the finish time of meeting i. Return the maximum number of meetings that can be accommodated in a single meeting room, when only one meeting can be held in the meeting room at a particular time. 

Note: The start time of one chosen meeting can't be equal to the end time of the other chosen meeting.

## Example
Input: start[] = [1, 3, 0, 5, 8, 5], end[] =  [2, 4, 6, 7, 9, 9]

Output: 4

Explanation: Maximum four meetings can be held with given start and end timings. The meetings are - (1, 2), (3, 4), (5,7) and (8,9)
## PROGRAM:(Main.cpp)
```
struct meeting {
   int start;
   int end;
   int pos;
};
class Solution {
  public:
    bool static comparator(struct meeting m1, meeting m2) 
    {
        if (m1.end < m2.end) return true;
        else if (m1.end > m2.end) return false;
        else if (m1.pos < m2.pos) return true;
        return false;
     }
    int maxMeetings(vector<int>& start, vector<int>& end) 
    {
        int n=start.size();
        vector<meeting> meet(n);
        
        for(int i=0;i<n;i++)
        {
            meet[i].start=start[i];
            meet[i].end=end[i];
            meet[i].pos=i+1;
        }
        
        sort(meet.begin(), meet.end(), comparator);
        vector < int > answer;
        int endtime = meet[0].end;
        int cnt=1;
        answer.push_back(meet[0].pos);

        for(int i = 1; i < n; i++) 
        {
           if (meet[i].start > endtime) 
           {
             endtime = meet[i].end;
             cnt++;
             answer.push_back(meet[i].pos);
           }
        }
        return cnt;
    }
};
```
## Complexity
- Time complexity : O(2N + N logN)

- Space complexity : O(3*N) + if they ask to return the position O(N) 
