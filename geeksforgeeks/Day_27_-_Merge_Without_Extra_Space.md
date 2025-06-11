# Day 27 - Merge Without Extra Space

Given two sorted arrays a[] and b[] of size n and m respectively, the task is to merge them in sorted order without using any extra space. Modify a[] so that it contains the first n elements and modify b[] so that it contains the last m elements.

Examples:

Input: a[] = [2, 4, 7, 10], b[] = [2, 3]
Output:
2 2 3 4
7 10
Explanation: After merging the two non-decreasing arrays, we get, 2 2 3 4 7 10
Input: a[] = [1, 5, 9, 10, 15, 20], b[] = [2, 3, 8, 13]
Output:
1 2 3 5 8 9
10 13 15 20
Explanation: After merging two sorted arrays we get 1 2 3 5 8 9 10 13 15 20.

Input: a[] = [0, 1], b[] = [2, 3]
Output:
0 1
2 3
Explanation: After merging two sorted arrays we get 0 1 2 3.

Constraints:
1 <= a.size(), b.size() <= 105
0 <= a[i], b[i] <= 107

### Code:
```java
...// } Driver Code Ends


// User function Template for Java

class Solution {
    // Function to merge the arrays.
    public void mergeArrays(int a[], int b[])
    {
        int n=a.length;
         int m=b.length;
         int gap=nextGap(n+m);
         while(gap >0)
         {
             int i,j;
             for(i=0;i+gap<n;i++)
             {
                 if(a[i]> a[i+gap])
                 {
                     int temp=a[i];
                     a[i]=a[i+gap];
                     a[i+gap]=temp;
                 }
             }
             
             for(j=gap > n ?gap-n :0;i<n && j<m ; i++,j++)
             {
                 if(a[i]> b[j])
                 {
                     int temp=a[i];
                     a[i]=b[j];
                     b[j]=temp;
                 }
             }
             
             if(j<m)
             {
                 for(j=0;j+gap < m;j++)
                 {
                     if(b[j] >b[j+gap])
                     {
                         int temp=b[j];
                         b[j]=b[j+gap];
                         b[j+gap]=temp;
                     }
                 }
             }
             gap=nextGap(gap);
             
         }
        
        
    }
    public int nextGap(int gap)
    {
        if(gap<=1)
         return 0;
         return (gap/2)+(gap%2);
```