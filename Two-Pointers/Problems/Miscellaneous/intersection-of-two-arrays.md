# [Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

Given two arrays, write a function to compute their intersection.


### Input 

    nums1 = [1,2,2,1]
    nums2 = [2,2]

### Output 

    [2,2]
    
-----------------------------------------------------------------

## Solution

- Using Two pointers ***one*** and ***two*** starting from 0.
- If the nums1[one] is equal to the nums2[two].Then, We will add the element to the answer, and increment one and two.
- Else If the nums1[one] is less than nums2[two] we increment one only.
- Else If the nums2[two] is less than nums1[one], we increment two only.
- Following the above conditions, Iterate over the array until one < length(nums1) and two < length(nums2). 

### Python Code

    class Solution:
        def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:

            nums1.sort()
            nums2.sort()

            answer = []
            one,two = 0,0

            while(one < len(nums1) and two < len(nums2)):
                if(nums1[one] == nums2[two]):
                    answer.append(nums1[one])
                    one += 1
                    two += 1
                elif(nums1[one] < nums2[two]):
                    one += 1
                else:
                    two += 1

            return answer
            
-----------------------------------------------------------------------

🎯 What is the time complexity of the above solution?

📝 ***O(N+M)*** where N is the size of nums1 and M is the size of nums2.

    As we are considering each element only once.
    
---------------------------------------------------------------------
