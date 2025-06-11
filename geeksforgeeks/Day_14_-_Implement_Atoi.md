# Day 14 - Implement Atoi

Given a string s, the objective is to convert it into integer format without utilizing any built-in functions. Refer the below steps to know about atoi() function.

Cases for atoi() conversion:

Skip any leading whitespaces.
Check for a sign (‘+’ or ‘-‘), default to positive if no sign is present.
Read the integer by ignoring leading zeros until a non-digit character is encountered or end of the string is reached. If no digits are present, return 0.
If the integer is greater than 231 – 1, then return 231 – 1 and if the integer is smaller than -231, then return -231.

Examples:

Input: s = "-123"
Output: -123
Explanation: It is possible to convert -123 into an integer so we returned in the form of an integer

Input: s = "  -"
Output: 0
Explanation: No digits are present, therefore the returned answer is 0.

Input: s = " 1231231231311133"
Output: 2147483647
Explanation: The converted number will be greater than 231 – 1, therefore print 231 – 1 = 2147483647.

Input: s = "-999999999999"
Output: -2147483648
Explanation: The converted number is smaller than -231, therefore print -231 = -2147483648.
Input: s = "  -0012gfg4"
Output: -12
Explanation: Nothing is read after -12 as a non-digit character ‘g’ was encountered.

Constraints:
1 ≤ |s| ≤ 15

### Code:
```java


class Solution {
    public int myAtoi(String s) 
    {
        int sign=1,res=0,i=0;
        while(i<s.length() && s.charAt(i)==' ')
        i++;
        s=s.substring(i);
        if(s.charAt(0)=='+')
        
        {
            sign=+1;
            i++;
            
        }
        else if(s.charAt(0)=='-')
        
        {
            sign=-1;
            i++;
            
        }
         while(i<s.length() && s.charAt(i)>='0' &&s.charAt(i)<='9')
         {
             if(res>Integer.MAX_VALUE/10 || res>Integer.MAX_VALUE/10 && (s.charAt(i)-'0')>7)
             return sign==1?Integer.MAX_VALUE:Integer.MIN_VALUE;
             res=res*10+(s.charAt(i++)-'0');
         }
         return res*sign;
        
    }
}
```