# Sliding Window Approach

A **sliding window** is a constant-size subarray that moves from left to right through the array.
At each window position, we want to calculate some information about the elements inside the window.

Sliding window is a sub-list that runs over an underlying data-structure e.g. Array, Strings etc.

Let's take an array:

    [ 1, 2, 3, 4, 5, 6, 7 ]

A **Sliding Window** of size 3 runs over the array like this:

    1 2 3

      2 3 4

        3 4 5

          4 5 6

            5 6 7
            
            
### Example

## Maximum Sum Sub-Array of Size K

We are given an array of size **N**. We need to calculate the maximum sum of **K** consecutive elements.

### Approach-1:

Finding all possible Sub-Arrays of size K and summing them up. Return the maximum sum out of those.

-----------------------------------------------------------
🎯 What's the time-complexity of this approach?

📝 ***O(N^2)*** 

    As we are generating each subarray and finding the sum of the elements in that subarray.
----------------------------------------------------------

### Approach-2:

Optimising the above approach using Sliding Window Approach.

1. Add the first **K** elements together, and store the sum in the variable ***currentSum***. Since this is the first sum, it is also the current maximum, so store it in variable ***maximumSum*** as well.

2. Since the window size is K, we slide the window one place to the right, and compute the sum of the elements in the window.

3. If the **currentSum** is larger than the **maximumSum**, then update the maximum and repeat step 2. 


        public static int maxSum(int[] arr, int k){

            int n = arr.length;
            int currentSum = 0;

            // Compute the initial sum of first K elements.
            for(int index = 0; index < k; index++)
                currentSum += arr[index];

            int maximumSum = currentSum;

            // Sliding the window and updating maximumSum
            for(int index = k; index < n; index++){
                // Add the rightmost element to the window and
                // discard the leftmost element from the window
                currentSum += arr[index] - arr[index-k];
                if(currentSum > maximumSum)
                    maximumSum = currentSum;
            }

            return maximumSum;

        }

------------ ----------------
🎯 What's the time complexity of the sliding window approach?

📝 ***O(n)***, 

    As we are iterating over the array only once.
--------------------------------

![](https://cdn-images-1.medium.com/max/1600/1*bREeaNhHy5SdiyUUMda4jA@2x.png)
