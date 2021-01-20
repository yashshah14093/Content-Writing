# BUILDHEAP OPERATION

-------------
📝Now Let's say you have an array of length n and you want to build a heap from its elements. So, which function you need to implement?

🎯Hoping, you got this correctly. We need to pass the array as a parameter into the buildHeap function to construct🔨 a heap of that array. 

--------------
- #### buildHeap

In this operation an unordered array is passed as a parameter which is transformed into an ordered heap. In this operation an heapify operation is performed on all the non-leaf nodes to order them in a correct priority.

Have a look at the animation below:

![buildHeap Operation](https://i.imgur.com/kHRNzFQ.gif)

Let's implement this operation:

    public void buildHeap(int[] arr){

        size = arr.length;
        // Copy elements of array arr to heaparray heap
        for(int i = 0; i < size; i++)
            heap[i] = arr[i];

        // building heap of heaparray 'heap'
        for(int i = (size/2); i >= 0; i--)
            heapify(i);
    }
    
**Time-Complexity**: To calculate time-complexity, We need to find the number of swap operation for the complete binary tree with N nodes. In the worst case the number of swap operations for a node is the height of its subtree which is *O(h)*. The number of nodes at height *h* is <= 2^floor(log(n))/2^h <= n/2^h. Therefore, the cost of heapifying all subtrees is:

![buildHeap Operation](https://i.imgur.com/ijUzHcn.jpg)

This uses the fact that the given infinite series ![buildHeap Operation](https://wikimedia.org/api/rest_v1/media/math/render/svg/c346abeef6557578d06d71e709ff29c9e96a6f49) converges.
