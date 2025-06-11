# Day 21 - Sort 0s, 1s and 2s

Given an array arr[] containing only 0s, 1s, and 2s. Sort the array in ascending order.

You need to solve this problem without utilizing the built-in sort function.

Examples:

Input: arr[] = [0, 1, 2, 0, 1, 2]
Output: [0, 0, 1, 1, 2, 2]
Explanation: 0s 1s and 2s are segregated into ascending order.
Input: arr[] = [0, 1, 1, 0, 1, 2, 1, 2, 0, 0, 0, 1]
Output: [0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 2, 2]
Explanation: 0s 1s and 2s are segregated into ascending order.

Follow up: Could you come up with a one-pass algorithm using only constant extra space?

Constraints:
1 <= arr.size() <= 106
0 <= arr[i] <= 2

### Code:
```java
...// } Driver Code Ends

class Solution {
    // Function to sort an array of 0s, 1s, and 2s
    public void sort012(int[] arr)
    {
        
       int n=arr.length;
       int low=0;
       int high=n-1;
       int mid=0,temp=0;
       while(mid<=high)
       {
           if(arr[mid] == 0)
           {
               swap(arr,mid,low);
               low++;
               mid++;
           }
           else if(arr[mid]==1)
           mid++;
           else
           {
               swap(arr,mid,high);
               high--;
           }
       }
       
       
        
    }
    static void swap(int[]a,int i, int j)
    {
      int temp=a[i];
      a[i]=a[j];
      a[j]=temp;
    }
    
    
    
}

...// } Driver Code Ends
```