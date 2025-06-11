# Day 15 - Add Binary Strings

Given two binary strings s1 and s2 consisting of only 0s and 1s. Find the resultant string after adding the two Binary Strings.
Note: The input strings may contain leading zeros but the output string should not have any leading zeros.

Input: s1 = "1101", s2 = "111"
Output: 10100
Explanation:
 1101
+ 111
10100

Input: s1 = "00100", s2 = "010"
Output: 110
Explanation: 
  100
+  10
  110


Constraints:
1 ≤s1.size(), s2.size()≤ 106

### Code:
```java


// User function Template for Java

class Solution
{
    public String addBinary(String s1, String s2) 
    {
        s1=trimzero(s1);
        s2=trimzero(s2);
        int n=s1.length();
   int m=s2.length();
        StringBuilder result=new StringBuilder();
        if(n<m)
        {
            return addBinary(s2,s1);
        }
        else
        {
            n=s1.length();
            m=s2.length();
            int j=m-1,sum=0,carry=0;
            for(int i=n-1;i>=0;i--)
            {
                sum=0;
                sum+=s1.charAt(i)-'0'+carry;
                if(j>=0)
                {
                    sum+=s2.charAt(j)-'0';
                    j--;
                }
                int bit=sum%2;
                carry=sum/2;
                result.append((char)(bit+'0'));
                
            }
            if(carry>0)
            result.append('1');
        }
        return result.reverse().toString();
    }
    
     public String trimzero(String s)
     {
         int one=s.indexOf("1");
         return one==-1?"0":s.substring(one);
     }
}
```