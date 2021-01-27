# [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

Given a string s, find the length of the longest substring without repeating characters.

### Input: 
    s = "abcabcbb"
    
### Output: 
    3
    
### Explanation: 
    The answer is "abc", with the length of 3.
    
----------------------------------------------------------------------
    
## Solution

- Two-Pointers
  - Use Map to store the frequency of characters.
  - Keep Two Pointers ***start*** and ***end*** which define the Substring having unique characters.
  - move the ***end*** pointer to scan through the string, While updating Map.
  - If the character is already in the Map, then move the ***start*** pointer to the right of the same character last found.
  
-----------------------------------------------
  
### Python Code

    class Solution:
        def lengthOfLongestSubstring(self, s: str) -> int:

            if(len(s) == 0):
                return 0

            # Two-Pointers
            start,end = 0,0

            # dictionary to store indices of the characters
            dt = {}

            # Variable to store maximum length
            max_length = 0

            while(end < len(s)):

                character = s[end]
                while(dt.get(character,0) > 0):
                    dt[s[start]] -= 1
                    start += 1

                dt[character] = dt.get(character,0) + 1
                max_length = max(max_length,end-start+1)
                end += 1


            return max_length
            
            
  -----------------------------------------------------
  
🎯 What is the time complexity of the above solution?

📝 ***O(N)***

    As we are considering each character only twice.
    
 --------------------------------------------------------
