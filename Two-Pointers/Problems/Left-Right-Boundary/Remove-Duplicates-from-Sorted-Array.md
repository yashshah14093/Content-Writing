# [ Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)


Given a sorted array nums, remove the duplicates in-place such that each element appears only once and returns the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

### Input

nums = [1,1,2]

### Output

2, nums = [1,2]

### Explanation

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively. It doesn't matter what you leave beyond the returned length.

-------------------------------------------------------------------------

## Solution

1. The array is already sorted.
2. Use Two pointers, ***one*** and ***two***.
3. If nums[one]=nums[two], Increment two to skip the duplicate.
4. Else Swap the nums[two] with nums[one+1] and Increment both one and two.
5. Repeat from Step-3.

### Python Code

    class Solution:
        def removeDuplicates(self, nums: List[int]) -> int:

            if(len(nums) == 0):
                return 0

            n = len(nums)
            one,two = 0,0

            while(two < n):
                # Step-3
                if(nums[one] == nums[two]):
                    two += 1
                # Step-4
                else:
                    nums[one+1] = nums[two]
                    one += 1
                    two += 1

            # return the length of the unique numbers
            return one + 1
            
         
🎯 What's the time complexity of this approach?

📝 ***O(N)*** 
   
    Iteration over the array only once.
