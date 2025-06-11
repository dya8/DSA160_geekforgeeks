# Day 6 - Majority Element II

You are given an array of integer arr[] where each number represents a vote to a candidate. Return the candidates that have votes greater than one-third of the total votes, If there's not a majority vote, return an empty array. 

Note: The answer should be returned in an increasing format.

Examples:

Input: arr[] = [2, 1, 5, 5, 5, 5, 6, 6, 6, 6, 6]
Output: [5, 6]
Explanation: 5 and 6 occur more n/3 times.
Input: arr[] = [1, 2, 3, 4, 5]
Output: []
Explanation: o candidate occur more than n/3 times.

Constraint:
1 <= arr.size() <= 106
-109 <= arr[i] <= 109

### Code:
```java
...// } Driver Code Ends


class Solution {
    // Function to find the majority elements in the array
    public List<Integer> findMajority(int[] nums) 
    {
        List<Integer>ar=new ArrayList<>();
        HashMap<Integer,Integer> hm=new HashMap<>();
        int n=nums.length;
        for(int a:nums)
        {
            if(hm.containsKey(a))
            
                hm.put(a,hm.get(a)+1);
            else
                hm.put(a,1);
            
             
        }
       int a=n/3;
            for(Map.Entry<Integer,Integer> entry:hm.entrySet())
            {
                if(entry.getValue()>a)
                ar.add(entry.getKey());
            }
           return ar;
        }
 
    }



```