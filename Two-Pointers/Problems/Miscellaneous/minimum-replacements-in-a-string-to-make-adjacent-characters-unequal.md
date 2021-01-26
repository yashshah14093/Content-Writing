# [Minimum replacements in a string to make adjacent characters unequal](https://www.geeksforgeeks.org/minimum-replacements-in-a-string-to-make-adjacent-characters-unequal/)

- Given a lowercase characters string str of size N. 
- In one operation any character can be changed into some other character. 
- The task is to find the minimum number of operations such that no two adjacent characters are equal.

### Input

    Str = “caaab” 

### Output

    1
    
### Explanation

    - Change the second a to any other character, let’s change it to b. 
    - So the string becomes “cabab”. and no two adjacent characters are equal. 
    - So minimum number of operations is 1.

---------------------------------------------------------------

## Solution

- Two-Pointer Approach
  - Initialize two pointers ***start*** and ***end*** as 0.
  - Increment end till the String[start] equals to String[end].
  - Now the number of operations you need to perform is the floor((end - start)/2).
  - Equate start to end as well to check new substring.
  - Return the count of all operations.
  
### Python Code

      def count_minimum(String): 

          n = len(String)  
          answer = 0
          start,end = 0,0

          while start < n: 

              while end < n and (String[end] == String[start]): 
                  end += 1

              answer += (end - start) // 2
              start = end

          return answer


      if __name__=="__main__": 

          String = "caaab"
          count_minimum(String) 
          
  -------------------------------------------------------------
  
  
🎯 What is the time complexity of the above solution?

📝 ***O(N)***

    As we are considering each character only once.
    
-------------------------------------------------------------------
