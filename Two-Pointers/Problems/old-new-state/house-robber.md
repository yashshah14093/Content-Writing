# [House Robber](https://leetcode.com/problems/house-robber/)

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

### Input: 
    nums = [1,2,3,1]
### Output: 
    4
### Explanation: 
     Rob house 1 (money = 1) and then rob house 3 (money = 3).
     Total amount you can rob = 1 + 3 = 4.
     
-----------------------------------------------------

## Solution

A robber has 2 options: 

      A) rob current house i; 
      B) don't rob current house.
      
#### Option-A
    
    Robber can't rob previous i-1 house but can safely proceed to the one before previous i-2 and gets all cumulative loot.
    
#### Option-B

    Robber gets all the possible loot from robbery of i-1.
    
    
So it boils down to calculating what is more profitable:

    - robbery of current house + loot from houses before the previous
    - loot from the previous house robbery and any loot captured before that
    
### Recursive Formula

    f(0) = nums[0]
    f(1) = max(nums[0], nums[1])
    f(k) = max( f(k-2) + nums[k], f(k-1) )
    
### Using Two-Pointers

- Using Two-Pointers ***last_second*** and ***last*** to refer the maximum profit till (index-2) and (index-1).
- For the current element, Calculate maximum profit possible by considering either last index (index-1) or Sum of the last_second index (index-2) and current element.
- Return maximum profit possible from the array of houses.

------------------------------------------------

### Python Code
    class Solution:
        def rob(self, nums: List[int]) -> int:

            last_second,last = 0,0

            for value in nums:
                last_second,last = last, max(last_second+value,last)

            return last
            
-------------------------------------------


🎯 What is the time complexity of the above solution?

📝 ***O(N)***

    As we are considering each house only once.
    
---------------------------------------------------
