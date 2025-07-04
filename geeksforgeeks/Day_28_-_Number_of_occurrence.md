# Day 28 - Number of occurrence

Given a sorted array, arr[] and a number target, you need to find the number of occurrences of target in arr[]. 

Examples :

Input: arr[] = [1, 1, 2, 2, 2, 2, 3], target = 2
Output: 4
Explanation: target = 2 occurs 4 times in the given array so the output is 4.
Input: arr[] = [1, 1, 2, 2, 2, 2, 3], target = 4
Output: 0
Explanation: target = 4 is not present in the given array so the output is 0.

Input: arr[] = [8, 9, 10, 12, 12, 12], target = 12
Output: 3
Explanation: target = 12 occurs 3 times in the given array so the output is 3.

Constraints:
1 ≤ arr.size() ≤ 106
1 ≤ arr[i] ≤ 106
1 ≤ target ≤ 106

### Code:
```java

class Solution {
    int countFreq(int[] arr, int target) 
    {
       int first = firstOccur(arr,target);
       if(first == -1)
       return 0;
       int last = lastOccur(arr,target);
       return last-first +1;
    }
    int firstOccur(int[] arr,int target)
    {
        int low=0,high =arr.length-1,result =-1;
        while(low <= high)
        {
            int mid = low +(high - low)/2;
            if(arr[mid]== target)
            {
                result=mid;   //for left 
                high=mid - 1;
                
            }
            else if(arr[mid] < target )
            {
                low = mid + 1;
            }
            else
            {
                high = mid - 1;
            }
        }
        return result;
    }
       int lastOccur(int[] arr,int target)
    {
        int low=0,high =arr.length-1,result =-1;
        while(low <= high)
        {
            int mid = low +(high - low)/2;
            if(arr[mid]== target)
            {
                result=mid;
                low=mid + 1;
                
            }
            else if(arr[mid] < target )  // for right
            {
                low = mid + 1;
            }
            else
            {
                high = mid - 1;
            }
        }
        return result;
    }
}

```