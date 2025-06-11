# Day 17 - Non Repeating Character

Given a string s consisting of lowercase English Letters. Return the first non-repeating character in s.
If there is no non-repeating character, return '$'.
Note: When you return '$' driver code will output -1.

Examples:

Input: s = "geeksforgeeks"
Output: 'f'
Explanation: In the given string, 'f' is the first character in the string which does not repeat.
Input: s = "racecar"
Output: 'e'
Explanation: In the given string, 'e' is the only character in the string which does not repeat.
Input: s = "aabbccc"
Output: -1
Explanation: All the characters in the given string are repeating.

Constraints:
1 ≤ s.size() ≤ 105

### Code:
```java


class Solution {
    static char nonRepeatingChar(String s) {
        HashMap<Character,Integer> count=new HashMap<>();
        for(char ch:s.toCharArray())
        {
            count.put(ch,count.getOrDefault(ch,0)+1);
        }
         for(char ch:s.toCharArray())
        {
           if(count.get(ch)==1)
           return ch;
        }
        return '$';
        
    }
}

```