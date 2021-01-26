# [Sum Of Four Numbers](https://www.geeksforgeeks.org/find-four-elements-that-sum-to-a-given-value-set-2/)

Given an array nums of n integers and an integer target, are there elements a, b, c, and d in nums such that a + b + c + d = target? 

Find a quadruplet in the array which gives the sum of target.

### Input

nums = [1,0,-1,0,-2,2], target = 0

### Output

[-2, -1, 1, 2]

------------------------------------------------------------------

## Solution

### Approach-1

We can use Four nested loops to iterate through the array and select the elements summing up to the target.

🎯 What's the time complexity of this approach?

📝 **O(N^4)** 

---------------------------------------

### Approach-2

- Assuming Array as 0-indexed and consisting of N elements.
- Use two pointers ***one*** and ***two*** to iterate over the array in the range of indices 0 and N-3.
- Then apply Two-Sum approach on the remaining elements from indices ***two+1*** till ***N-1*** to find the remaining target sum.
- If the Sum equal to target is found, return the List of those elements.

🎯 What's the time complexity of this approach?

📝 ***O(N^3)***

    Three Nested Loops:
    - One Loop for Pointer ***one***
    - One Loop for Pointer ***two***
    - One Loop for Two-Sum Approach
    
-----------------------------------------------------

#### Python Code

    class Solution:

        def twoSum(self,nums,target,low,high):
            # Using Two Sum Approach to find elements summing up to target
            while(low < high):
                if(nums[low] + nums[high] == target):
                    return [nums[low],nums[high]]
                elif(nums[low] + nums[high] < target):
                    low += 1
                else:
                    high -= 1

            return False


        def solve(self, nums, k):

            n = len(nums)
            nums.sort()

            # Pointer one
            for one in range(n-3):
                # Pointer two
                for two in range(one+1,n-2):

                    # target is the remaining sum
                    target = k - nums[one] - nums[two]

                    # Finding  if the remaining elements exits with sum equal to target
                    rem = self.twoSum(nums,target,two+1,n-1)

                    # If four elements exist with sum equal to k
                    if(rem):
                        answer = [nums[one],nums[two]] + rem
                        return answer

            return False
