# [Interval Overlaps](https://binarysearch.com/problems/Interval-Overlaps)

- You are given a list of closed intervals ***l0*** and another list of intervals ***l1***. 
- Individually, each list is non-overlapping and are sorted in ascending order.
- Return the overlap of the two intervals sorted in ascending order.

### Input

l0 = [
    [1, 3],
    [5, 6],
    [7, 9]
]

l1 = [
    [1, 4],
    [5, 7]
]

### Output

[
    [1, 3],
    [5, 6],
    [7, 7]
]

------------------------------------

## Solution

- Traverse both intervals using pointers ***one*** and ***two***.
- Find maximum start and minimum end of both intervals referenced by ***one*** and ***two***.
- For e.g. one = [1, 4], two = [2, 6] - max start is 2 and min end is 4 that will be result candidate.
- Remove the smallest end by incrementing ***one*** or ***two***. As the smallest end can't intersect with any of the interval in further traversal.

### Python Code

    class Solution:
        def solve(self, l0, l1):

            one = 0
            two = 0
            ans = []

            while(one < len(l0) and two < len(l1)):

                maxStart = max(l0[one][0],l1[two][0])
                minEnd   = min(l0[one][1],l1[two][1])

                if(maxStart <= minEnd):
                    ans.append([maxStart,minEnd])

                if(l0[one][1] <= l1[two][1]):
                    one += 1
                else:
                    two += 1


            return ans
            
--------------------------------------------------------------


🎯 What is the time complexity of the above solution?

📝 ***O(N + M)*** where N is the number of intervals in l0 and M is the number of intervals in l1.

    As we are considering each interval only once.

--------------------------------------------------------
