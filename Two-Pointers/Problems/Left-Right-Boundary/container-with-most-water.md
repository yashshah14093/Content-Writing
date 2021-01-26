# [Container With Most Water](https://leetcode.com/problems/container-with-most-water/)

- Given N non-negative integers A1, A2, ..., An , where each represents a point at coordinate (i, Ai). 
- N vertical lines are drawn such that the two endpoints of the line i is at (i, Ai) and (i, 0).
- Find two lines, which, together with the X-axis forms a container, such that the container contains the most water.

### Input 

height = [1,8,6,2,5,4,8,3,7]

### Output

49

-----------------------------------------------------

## Solution

### Approach-1

- Consider the area for every possible pair of the lines.
- Find out the maximum area out of those.

#### Python Code

    class Solution:
        def maxArea(self, height: List[int]) -> int:

            n = len(height)
            maxArea = 0

            for i in range(n):
                for j in range(i+1,n):
                    dist = min(height[i],height[j])*(j-i)
                    maxArea = max(maxArea,dist)

            return maxArea
            
 -----------------------------------------------------------           
            
🎯 What is the time complexity of Approach-2?

📝 ***O(N^2)*** 
    
    As we are considering all the containers N times with each of the other container in the array.
    
--------------------------------------------------------------     
     
### Approach-2

#### Idea

- The widest container (using first and last line) is a good candidate, because of its width.
- Water level is the height of the smaller one of first and last line.
- All other containers are less wide and thus would need a higher water level in order to hold more water.
- The smaller one of first and last line doesn't support a higher water level and can thus be safely removed from further consideration.

#### Implementation

- Variables/Pointers i and j define the container under consideration. We initialize them to first and last line, meaning the widest container.
- Variable water will keep track of the highest amount of water we managed so far.
- We compute j - i, the width of the current container, and min(height[i], height[j]), the water level that this container can support.
- Multiply them to get how much water this container can hold, and update water accordingly. 
- Next remove the smaller one of the two lines from consideration as described in the idea.
- Continue until there is nothing left to consider, then return the result.

#### Python Code

    class Solution:
        def maxArea(self, height):
            i, j = 0, len(height) - 1
            water = 0
            while i < j:
                water = max(water, (j - i) * min(height[i], height[j]))
                if height[i] < height[j]:
                    i += 1
                else:
                    j -= 1
            return water
            
---------------------------------------------------

🎯 What is the time complexity of Approach-2?

📝 ***O(N)***

    As we are considering each container only once.
    
 -----------------------------------------------
