## Minimum Platforms  (c++)

You are given the arrival times arr[] and departure times dep[] of all trains that arrive at a railway station on the same day. Your task is to determine the minimum number of platforms required at the station to ensure that no train is kept waiting.

At any given time, the same platform cannot be used for both the arrival of one train and the departure of another. Therefore, when two trains arrive at the same time, or when one arrives before another departs, additional platforms are required to accommodate both trains.
## Example
Input: arr[] = [900, 940, 950, 1100, 1500, 1800], dep[] = [910, 1200, 1120, 1130, 1900, 2000]

Output: 3

Explanation: There are three trains during the time 9:40 to 12:00. So we need a minimum of 3 platforms.
## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    int findPlatform(vector<int>& arr, vector<int>& dep) 
    {
        sort(arr.begin(),arr.end());
        sort(dep.begin(),dep.end());
        int n=arr.size();
        int max_cnt=0;
        int cnt=0;
        int l=0,r=0;
        
        while(l<n)
        {
            if(arr[l]<=dep[r])
            {
                cnt++;
                l++;
            }
            else
            {
                cnt--;
                r++;
            }
            max_cnt=max(max_cnt,cnt);
        }
        return max_cnt;
    }
};
```
## Complexity
- Time complexity : O(2(NlogN + N))

- Space complexity : O(1) 
