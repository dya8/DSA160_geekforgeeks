# Day 37 - Rotate by 90 degree

Given a square matrix mat[][] of size n x n. The task is to rotate it by 90 degrees in an anti-clockwise direction without using any extra space. 

Examples:

Input: mat[][] = [[1, 2, 3],
                [4, 5, 6]
                [7, 8, 9]]
Output: Rotated Matrix:
[3, 6, 9]
[2, 5, 8]
[1, 4, 7]

Input: mat[][] = [[1, 2],
                [3, 4]]
Output: Rotated Matrix:
[2, 4]
[1, 3]

Constraints:
1 ≤ n ≤ 102
0 <= mat[i][j] <= 103

### Code:
```java
...// } Driver Code Ends


// User function Template for Java

class Solution 
{
    // Function to rotate matrix anticlockwise by 90 degrees.
    static void rotateby90(int mat[][])
    {
        int n=mat.length;
       for(int i=0;i<n;i++)
       {
           for(int j=i+1;j<n;j++)
           {
               int temp=mat[i][j];
              mat[i][j]=mat[j][i];
               mat[j][i]=temp;
           }
       }
       for(int col=0;col<n;col++)
       {
           int top=0,bottom=n-1;
           while(top<bottom)
           {
               int temp=mat[top][col];
              mat[top][col]=mat[bottom][col];
              mat[bottom][col]=temp;
              top++;
              bottom--;
              
           }
       }
    }
    public static void printMatrix(int[][]mat,int n)
    {
        for(int[] row:mat)
        {
            for(int val:row)
            {
                System.out.print(val+" ");
                
            }
            System.out.println();
        }
    }
}
```