# [Angry Owner](https://binarysearch.com/problems/Angry-Owner)

- You are given two lists of integers customers and mood, both of them the same length, and an integer k. 
- On each minute i, customers[i] number of people come to the store and if mood[i] = 1, then the customers are happy whereas if mood[i] = 0, then they are unhappy.
- Given that you can set a sublist of length k of mood to 1s, return the maximum number of people you can make happy.


### Input
    customers = [1, 2, 5, 5, 2]
    mood = [1, 1, 0, 0, 0]
    k = 2
    
### Output
    13
    
-------------------------------------------------------------------

## Solution

### Sliding Window Approach

   ***Step-1***: Dividing the problem into two smaller problems.
   
   ***Step-2***: Count how many customers are already satisfied. Remove those customers by assigning 0.
   
   ***Step-3***: Now we are left with only the currently unhappy customers in the list.
   
   ***Step-4***: We can make k adjacent customers happy. For that we can use the sliding window approach to find the maximum sum of k-size subarray of customers.
   
   ***Step-5***: Answer will be the result of step-2 and step-4.


### Python Code

    class Solution:
        def solve(self, customers, mood, k):

            # Counting how many customers are already happy, and removing them from the customer list.
            already_happy = 0
            for index in range(len(mood)):
                if(mood[index] == 1):
                    already_happy += customers[index]
                    customers[index] = 0

            # finding the optimal number of unhappy customers we can make happy.
            optimalMax = 0
            current_happy = 0
            for index,cust in enumerate(customers):
                current_happy += cust
                if(index >= k):
                    current_happy -= customers[index-k]
                optimalMax = max(optimalMax,current_happy)

            # Answer
            return already_happy + optimalMax

-----------------------------------------

🎯 What is the time complexity of the above solution?

📝 ***O(N)***

    As we are considering each customer only Two times.
    
-----------------------------------------------------
