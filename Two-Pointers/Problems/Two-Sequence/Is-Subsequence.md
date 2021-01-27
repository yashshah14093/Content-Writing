# [Is Subsequence](https://leetcode.com/problems/is-subsequence/)

- Given a string s and a string t, check if s is subsequence of t.

- A subsequence of a string is a new string which is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (ie, "ace" is a subsequence of "abcde" while "aec" is not).

### Input: 
    s = "abc", t = "ahbgdc"
### Output: 
    true
    
---------------------------------------------------

## Solution

- Use Two Pointers ***one*** and ***two***.
- ***one*** refers to String **s** character.
- ***two*** refers to String **t** character.
- if character at **one** equals to character at **two**, increment one and two.
- else increment two.
- If one equals to the length of String s, then return true. That means all characters of s can be found in t maintaining the order.
- else return false.

----------------------------------------------------------

### Python Code

    class Solution:
        def isSubsequence(self, s: str, t: str) -> bool:

            one,two = 0,0

            while(one < len(s) and two < len(t)):
                if(s[one] == t[two]):
                    one += 1
                two += 1

            return one == len(s)
            
-----------------------------------------------------


🎯 What is the time complexity of the above solution?

📝 ***O(N+M)*** where N is the number of character in String s and M is the number of characters in String t.

    As we are considering each character only once in t as well as s.
    
-------------------------------------------------------------
