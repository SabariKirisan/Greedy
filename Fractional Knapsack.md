## Fractional Knapsack  (c++)

Given two arrays, val[] and wt[], representing the values and weights of items, and an integer capacity representing the maximum weight a knapsack can hold, determine the maximum total value that can be achieved by putting items in the knapsack. You are allowed to break items into fractions if necessary.
Return the maximum value as a double, rounded to 6 decimal places.
## Example
Input: val[] = [60, 100], wt[] = [10, 20], capacity = 50

Output: 160.000000

Explanation: Take both the items completely, without breaking. Total maximum value of item we can have is 160.00 from the given capacity of sack.
## PROGRAM:(Main.cpp)
```
struct Item
{
    int value;
    int weight;
};

class Solution 
{
  public:
    bool static comp(Item a, Item b) 
    {
        double r1 = (double) a.value / (double) a.weight;
        double r2 = (double) b.value / (double) b.weight;
        return r1 > r2;
     }
    double fractionalKnapsack(vector<int>& val, vector<int>& wt, int capacity) 
    {
        int n = val.size();
        vector<Item> items(n);
        for(int i = 0; i < n; i++) 
        {
            items[i].value = val[i];
            items[i].weight = wt[i];
        }

        sort(items.begin(), items.end(), comp);

        double totalValue = 0.0;

        for (int i = 0; i < n; i++) 
        {
            if (capacity >= items[i].weight) 
            {
                totalValue += items[i].value;
                capacity -= items[i].weight;
            } else 
            {
                totalValue += ((double)items[i].value / items[i].weight) * capacity;
                break;
            }
        }
        return round(totalValue * 1e6) / 1e6;
    }
};
```
## Complexity
- Time complexity : O(N + NlogN)

- Space complexity : O(1) 
