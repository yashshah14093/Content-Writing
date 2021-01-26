# [Find a subarray of size K whose sum is a perfect square](https://www.geeksforgeeks.org/find-a-subarray-of-size-k-whose-sum-is-a-perfect-square/)

## Problem Statement

- Given an array arr[] and an integer K. 
- The task is to find a subarray of length K having sum which is a perfect square. 
- If no such subarray exists, then print -1. Otherwise, print the subarray.

#### Input

arr[] = {20, 34, 51, 10, 99, 87, 23, 45}

K = 3 

#### Output

{10, 99, 87} 

----------------------------------------------------

## Solution:

### Approach-1

- Generate all possible Subarrays of size K.
- Check whether the sum of any Subarray generated is a perfect square or not.

----------------------------------------------

🎯 What is the time complexity of the above solution?

📝 ***O(N*K)***

    As we are considering a Subarray of size K for each index.
    
---------------------------------------------------

### Approach-2

- Using Sliding Window Technique
  1. Calculate the sum of first K array elements using variable ***curr_sum***.
  2. Iterate over the remaining array elements while updating ***curr_sum*** -> Add ith index element to curr_sum and remove the (i-K)th element.
  3. For each calculated curr_sum, find whether it is prime or not.
  4. If any prime value is found, then that subarray will be the answer else -1.
  
  #### Python Code
  
          from math import sqrt, ceil, floor

          def isPerfectSquare(n):

              # Find square root of n
              sr = sqrt(n)

              # Check if the square root is an integer or not
              return ((sr - floor(sr)) == 0)


          
          def SubarrayHavingPerfectSquare(arr, k):

              sum = 0

              # Sum of first K elements
              i = 0
              while i < k:
                  sum += arr[i]
                  i += 1

              # If the first k elements have a sum as perfect square
              if (isPerfectSquare(sum)):
                  return arr[0:k]

              else:

                  # Iterate through the array
                  for j in range(i, len(arr)):
                      sum = sum + arr[j] - arr[j - k]

                      # If sum is perfect square
                      if (isPerfectSquare(sum)):
                          return arr[j - k + 1:j+1]
                  
                  # If No Subarray is found
                  return -1

       
          if __name__ == '__main__':

              arr = [ 20, 34, 51, 10, 99, 87, 23, 45 ]
              K = 3

              SubarrayHavingPerfectSquare(arr, K)
              
-----------------------------

🎯 What is the time complexity of the above solution?

📝 ***O(N)***

    As we are considering elements of array only once.
    
-----------------------------------------------------------
