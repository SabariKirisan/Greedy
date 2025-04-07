## Shortest Job first (c++)

Geek is a software engineer. He is assigned with the task of calculating average waiting time of all the processes by following shortest job first policy.

The shortest job first (SJF) or shortest job next, is a scheduling policy that selects the waiting process with the smallest execution time to execute next.

Given an array of integers bt of size n. Array bt denotes the burst time of each process. Calculate the average waiting time of all the processes and return the nearest integer which is smaller or equal to the output.

Note: Consider all process are available at time 0.

## Example
Input:n = 5 bt = [4,3,7,1,2]

Output: 4

Explanation: After sorting burst times by shortest job policy, calculated average waiting time is 4.
## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    long long solve(vector<int>& bt) 
    {
        int n=bt.size();
        sort(bt.begin(),bt.end());
        int t=0,waittime=0;
        
        for(int i=0;i<n;i++)
        {
            waittime+=t;
            t+=bt[i];
        }
        return (waittime/n);
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(1)
