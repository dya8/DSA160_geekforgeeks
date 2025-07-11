# Day 26 - Non-overlapping Intervals

Given a 2D array intervals[][] of representing intervals where intervals [i] = [starti, endi ]. Return the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping.

Examples:

Input: intervals[][] = [[1, 2], [2, 3], [3, 4], [1, 3]]
Output: 1
Explanation: [1, 3] can be removed and the rest of the intervals are non-overlapping.
Input: intervals[][] = [[1, 3], [1, 3], [1, 3]]
Output: 2
Explanation: You need to remove two [1, 3] to make the rest of the intervals non-overlapping.
Input: intervals[][] = [[1, 2], [5, 10], [18, 35], [40, 45]]
Output: 0
Explanation: All ranges are already non overlapping.


Constraints:
1 ≤ intervals.size() ≤  105
|intervalsi| == 2
0 ≤ starti < endi <=5*104

### Code:
```java
...// } Driver Code Ends


// User function Template for Java

class Solution {
    static int minRemoval(int intervals[][])
    {
       Arrays.sort(intervals,(a,b) -> Integer.compare(a[1],b[1]));
       int count=0;
       int end=Integer.MIN_VALUE;
       for(int[]interval : intervals)
       {
           if(interval[0] >= end)
           {
               end=interval[1];
           }
           else
           {
               count++;
           }
       }
       return count;
    }
}

```