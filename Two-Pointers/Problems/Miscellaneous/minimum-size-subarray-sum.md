# [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)

Given an array of n positive integers and a positive integer s, find the minimal length of a contiguous subarray of which the sum ≥ s. If there isn't one, return 0 instead.

### Input 
    s = 7, nums = [2,3,1,2,4,3]

### Output
    2
    
### Explanation
    The subarray [4,3] has the minimal length under the problem constraint.
    
--------------------------------------------------------------------

## Solution

- Two-Pointers Method
  - Initialize the two pointers to 0. Call them start and end.
  - Now the idea is to move the end pointer until the point we have a solution.
  - At this point we want to shrink the solution by moving the start pointer right.
  - Return the minimum difference between start and end, satisfying the solution.
  
  
  
  ### Python Code
  
      class Solution:
        def minSubArrayLen(self, s: int, nums: List[int]) -> int:

            start,end = 0,0
            min_length = len(nums)+1
            curr_sum = 0 


            while(end < len(nums)):

                curr_sum += nums[end]

                while(curr_sum >= s):
                    min_length = min(min_length,end-start+1)
                    curr_sum -= nums[start]
                    start += 1

                end += 1


            if(min_length <= len(nums)):
                return min_length
            return 0
            
----------------------------------------------------------------------

🎯 What is the time complexity of the above solution?

📝 ***O(N)***

    As we are considering each element only once.
    
------------------------------------------------------
