# Day 12 - Max Circular Subarray Sum

Given an array of integers arr[] in a circular fashion. Find the maximum subarray sum that we can get if we assume the array to be circular.

Examples:

Input: arr[] = [8, -8, 9, -9, 10, -11, 12]
Output: 22
Explanation: Starting from the last element of the array, i.e, 12, and moving in a circular fashion, we have max subarray as 12, 8, -8, 9, -9, 10, which gives maximum sum as 22.
Input: arr[] = [10, -3, -4, 7, 6, 5, -4, -1]
Output: 23
Explanation: Maximum sum of the circular subarray is 23. The subarray is [7, 6, 5, -4, -1, 10].

Input: arr[] = [-1, 40, -14, 7, 6, 5, -4, -1] 
Output: 52
Explanation: Circular Subarray [7, 6, 5, -4, -1, -1, 40] has the maximum sum, which is 52.

Constraints:
1 <= arr.size() <= 105
-104 <= arr[i] <= 104

### Code:
```java


class Solution {

    // a: input array
    // n: size of array
    // Function to find maximum circular subarray sum.
    public int circularSubarraySum(int arr[]) 
    {
        int totalSum=0,currMaxSum=0,currMinSum=0,minsum=arr[0],maxsum=arr[0];
        int normalsum=0,n,i,circularsum=0;
        n=arr.length;
        for(i=0;i<n;i++)
        {
            currMaxSum=Math.max(currMaxSum +arr[i],arr[i]);
             currMinSum=Math.min(currMinSum +arr[i],arr[i]);
              maxsum=Math.max(maxsum,currMaxSum);
               minsum=Math.min(minsum,currMinSum);
               totalSum+=arr[i];
            
        }
          normalsum=maxsum;
          circularsum=totalSum-minsum;
          if(minsum==totalSum)
          return normalsum;
          else
          return Math.max(normalsum,circularsum);
      
    }
}

```