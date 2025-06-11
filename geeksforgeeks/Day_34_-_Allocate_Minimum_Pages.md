# Day 34 - Allocate Minimum Pages

You are given an array arr[] of integers, where each element arr[i] represents the number of pages in the ith book. You also have an integer k representing the number of students. The task is to allocate books to each student such that:

Each student receives atleast one book.
Each student is assigned a contiguous sequence of books.
No book is assigned to more than one student.

The objective is to minimize the maximum number of pages assigned to any student. In other words, out of all possible allocations, find the arrangement where the student who receives the most pages still has the smallest possible maximum.

Note: Return -1 if a valid assignment is not possible, and allotment should be in contiguous order (see the explanation for better understanding).

Examples:

Input: arr[] = [12, 34, 67, 90], k = 2
Output: 113
Explanation: Allocation can be done in following ways:
[12] and [34, 67, 90] Maximum Pages = 191
[12, 34] and [67, 90] Maximum Pages = 157
[12, 34, 67] and [90] Maximum Pages = 113.
Therefore, the minimum of these cases is 113, which is selected as the output.
Input: arr[] = [15, 17, 20], k = 5
Output: -1
Explanation: Allocation can not be done.

Input: arr[] = [22, 23, 67], k = 1
Output: 112

Constraints:
1 <=  arr.size() <= 106
1 <= arr[i] <= 103
1 <= k <= 103 

### Code:
```java



//Back-end complete function Template for Java

class Solution 
{
    public static int findPages(int[] arr, int k) 
    {
       int n=arr.length;
       if(k>n)
       return -1;
       int low=Integer.MIN_VALUE;
       int high=0;
       for(int pages : arr)
       {
           low=Math.max(low,pages);
           high+=pages;
       }
       int result=-1;
       while(low <= high)
       {
           int mid=low+(high-low)/2;
           if(isValid(arr,k,mid))
           {
               result=mid;
               high=mid-1;
           }
           else
           {
               low=mid+1;
           }
       }
       return result;
       
    }
    
        private static boolean isValid(int[]arr, int k, int maxPages)
        {
            int studct=1;
            int currS=0;
            for(int pages : arr)
            {
                if(currS+pages > maxPages)
                {
                    studct++;
                    currS=pages;
                    if(studct > k)
                    return false;
                
                }
                else
                currS+=pages;
            }
            return true;
        }
}
```