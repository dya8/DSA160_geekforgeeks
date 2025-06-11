# Day 10 - Kadane's Algorithm

Given an integer array arr[]. You need to find the maximum sum of a subarray.


Examples:

Input: arr[] = [2, 3, -8, 7, -1, 2, 3]
Output: 11
Explanation: The subarray {7, -1, 2, 3} has the largest sum 11.

Input: arr[] = [-2, -4]
Output: -2
Explanation: The subarray {-2} has the largest sum -2.
Input: arr[] = [5, 4, 1, 7, 8]
Output: 25
Explanation: The subarray {5, 4, 1, 7, 8} has the largest sum 25.

Constraints:
1 ≤ arr.size() ≤ 105
-109 ≤ arr[i] ≤ 104

### Code:
```java


class Solution {
    int maxSubarraySum(int[] arr) 
    {
        int n=arr.length,res=arr[0];
        int maxend=arr[0];
        for(int i=1;i<n;i++)
        {
            maxend=Math.max(maxend+arr[i],arr[i]);
            res=Math.max(res,maxend);
        }
        return res;
    }
}

```