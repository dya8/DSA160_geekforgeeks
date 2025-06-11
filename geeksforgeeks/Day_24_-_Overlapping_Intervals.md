# Day 24 - Overlapping Intervals

Given an array of Intervals arr[][], where arr[i] = [starti, endi]. The task is to merge all of the overlapping Intervals.

Examples:

Input: arr[][] = [[1,3],[2,4],[6,8],[9,10]]
Output: [[1,4], [6,8], [9,10]]
Explanation: In the given intervals we have only two overlapping intervals here, [1,3] and [2,4] which on merging will become [1,4]. Therefore we will return [[1,4], [6,8], [9,10]].

Input: arr[][] = [[6,8],[1,9],[2,4],[4,7]]
Output: [[1,9]]
Explanation: In the given intervals all the intervals overlap with the interval [1,9]. Therefore we will return [1,9].


Constraints:
1 ≤ arr.size() ≤ 105
0 ≤ starti ≤ endi ≤ 105

### Code:
```java
...// } Driver Code Ends


class Solution {
    public List<int[]> mergeOverlap(int[][] arr) 
    {
      
        List<int[]> result=new ArrayList<>();
       if(arr.length == 0)
       return result;
       Arrays.sort(arr,(a,b) -> Integer.compare(a[0],b[0]));
       int [] curr =arr[0];
       result.add(curr);
       for(int[] interval:arr)
       {
           int currEnd=curr[1];
           int nextStart=interval[0];
             int nextEnd=interval[1];
             if(currEnd >= nextStart)
             {
                 curr[1]=Math.max(currEnd,nextEnd);
             }
             else
             {
                 curr=interval;
                 result.add(curr);
             }
       }
       return result;
    }
}
```