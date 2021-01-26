# [Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)

Write a function that takes a string as input and reverse only the vowels of a string.

### Input

"edmad"

### Output

"admed"

---------------------------------------------------------------------------

## Solution

1. Consider Two pointers ***left*** and ***right***.
2. If String[left] is a consonant, then increment **left**.
3. Else If String[right] is a consonant, then decrement **right**.
4. Else the charcters at both left and right are vowels and left < right, Then swap those characters and increment left and right.

### Python Code

    class Solution:
        def reverseVowels(self, s: str) -> str:

            String = list(s)
            n = len(String)

            vowels = "aeiouAEIOU"

            # Step-1
            left,right = 0,n-1

            while(left < right):
                # Step-2
                if(String[left] not in vowels):
                    left += 1
                # Step-3
                elif(String[right] not in vowels):
                    right -= 1
                # Step-4
                else:
                    String[left],String[right] = String[right],String[left]
                    left += 1
                    right -= 1

            return "".join(String)

---------------------


🎯 What is the time complexity of the above solution?

📝 ***O(N)***

    As we are considering each character only once.
    
-------------------------------------
