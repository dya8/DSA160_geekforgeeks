# Day 20 - Strings Rotations of Each Other

You are given two strings of equal lengths, s1 and s2. The task is to check if s2 is a rotated version of the string s1.

Note: The characters in the strings are in lowercase.

Examples :

Input: s1 = "abcd", s2 = "cdab"
Output: true
Explanation: After 2 right rotations, s1 will become equal to s2.

Input: s1 = "aab", s2 = "aba"
Output: true
Explanation: After 1 left rotation, s1 will become equal to s2.

Input: s1 = "abcd", s2 = "acbd"
Output: false
Explanation: Strings are not rotations of each other.

Constraints:
1 <= s1.size(), s2.size() <= 105

### Code:
```java
...// } Driver Code Ends



class Solution {
    // Function to check if two strings are rotations of each other or not.
    public static boolean areRotations(String s1, String s2)
    {
        String txt=s1+s1;
        String pat=s2;
        int n=txt.length();
        int m=pat.length();
        int[]lps=LPSArray(pat);
        int i=0;
        int j=0;
        while(i<n)
        {
            if(pat.charAt(j) == txt.charAt(i))
            {
                j++;
                i++;
                
            }
            if(j == m)
            {
                    return true;
            }
            else if(i<n && pat.charAt(j)!= txt.charAt(i))
            {
                if(j!=0)
                j=lps[j-1];
                else
                i=i+1;
            }
        }
        return false;
       
    }
    static int[] LPSArray(String pat)
    {
        int n=pat.length();
        int[] lps=new int[n];
        int len=0;
        lps[0]=0;
        int i=1;
        while(i<n)
        {
            if(pat.charAt(i) == pat.charAt(len) )
            {
                len++;
                lps[i]=len;
                i++;
                
            }
            else
            {
                if(len!=0)
                {
                    len=lps[len -1];
                }
            
            else
            {
                lps[i]=0;
                i++;
            }
        }
    }
    return lps;
}
    
}
```