# Day 36 - Spirally traversing a matrix

You are given a rectangular matrix mat[][] of size n x m, and your task is to return an array while traversing the matrix in spiral form.

Examples:

Input: mat[][] = [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12], [13, 14, 15, 16]]
Output: [1, 2, 3, 4, 8, 12, 16, 15, 14, 13, 9, 5, 6, 7, 11, 10]
Explanation: 


Input: mat[][] = [[1, 2, 3, 4, 5, 6], [7, 8, 9, 10, 11, 12], [13, 14, 15, 16, 17, 18]]
Output: [1, 2, 3, 4, 5, 6, 12, 18, 17, 16, 15, 14, 13, 7, 8, 9, 10, 11]
Explanation: Applying same technique as shown above.
Input: mat[][] = [[32, 44, 27, 23], [54, 28, 50, 62]]
Output: [32, 44, 27, 23, 62, 50, 28, 54]
Explanation: Applying same technique as shown above, output will be [32, 44, 27, 23, 62, 50, 28, 54].

Constraints:
1 <= n, m <= 1000
0 <= mat[i][j]<= 100

### Code:
```java
...// } Driver Code Ends


class Solution {
    // Function to return a list of integers denoting spiral traversal of matrix.
    public ArrayList<Integer> spirallyTraverse(int mat[][]) 
    {
        ArrayList<Integer> result=new ArrayList<>();
        if(mat.length==0)
        return result;
        int top=0;
        int bottom=mat.length-1;
        int left=0;
        int right=mat[0].length-1;
        while(top <= bottom && left<=right)
        {
            for(int i=left;i<=right;i++)
            {
                result.add(mat[top][i]);
            }
            top++;
            for(int i=top;i<=bottom;i++)
            {
                result.add(mat[i][right]);
            }
            right--;
            if(top<=bottom)
            {
                for(int i=right;i>=left;i--)
                {
                    result.add(mat[bottom][i]);
                }
                bottom--;
            }
             
            if(left<=right)
            {
                for(int i=bottom;i>=top;i--)
                {
                    result.add(mat[i][left]);
                }
                left++;
            }
            
        }
        return result;
        
        
    }
}

```