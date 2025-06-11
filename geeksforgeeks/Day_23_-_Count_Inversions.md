# Day 23 - Count Inversions

Given an array of integers arr[]. Find the Inversion Count in the array.
Two elements arr[i] and arr[j] form an inversion if arr[i] > arr[j] and i < j.

Inversion Count: For an array, inversion count indicates how far (or close) the array is from being sorted. If the array is already sorted then the inversion count is 0.
If an array is sorted in the reverse order then the inversion count is the maximum. 

Examples:

Input: arr[] = [2, 4, 1, 3, 5]
Output: 3
Explanation: The sequence 2, 4, 1, 3, 5 has three inversions (2, 1), (4, 1), (4, 3).
Input: arr[] = [2, 3, 4, 5, 6]
Output: 0
Explanation: As the sequence is already sorted so there is no inversion count.
Input: arr[] = [10, 10, 10]
Output: 0
Explanation: As all the elements of array are same, so there is no inversion count.

Constraints:
1 ≤ arr.size() ≤ 105
1 ≤ arr[i] ≤ 104


### Code:
```java
...// } Driver Code Ends


// User function Template for Java

class Solution {
    // Function to count inversions in the array.
    static int countAndMerge(int arr[],int m,int l,int r)
    {
        
        int n1=m-l+1;
        int n2=r-m;
        int[] left=new int[n1];
        int[] right=new int[n2];
        for(int i=0;i<n1;i++)
         left[i]=arr[l+i];
        for(int j=0;j<n2;j++)
         right[j]=arr[m+1+j];
         
         int count=0;
         int i=0,j=0,k=l;
         while(i<n1 && j<n2)
         {
             if(left[i] <= right[j])
             arr[k++]=left[i++];
             else
             {
                 arr[k++]=right[j++];
                 count+=(n1-i);
             }
         }
          while(i<n1)
          arr[k++]=left[i++];
           while(j<n2)
          arr[k++]=right[j++];
          return count;
          
        
    }
    
    static int countInv(int[] arr,int l,int r)
    {
        int res=0;
        if(l<r)
        {
            int m=(l+r)/2;
            res+=countInv(arr,l,m);
            res+=countInv(arr,m+1,r);
            res+=countAndMerge(arr,m,l,r);
        }
        return  res;
    }
    static int inversionCount(int[] arr)
    {
        return countInv(arr,0,arr.length-1);
    }
}
```