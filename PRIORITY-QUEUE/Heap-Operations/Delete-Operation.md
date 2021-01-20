# Delete Operation
    
- #### Delete an element

Steps to delete an element:

1. Find the index of an element that we want to delete.

2. Swap that element with that index.

3. Decrement the size of heap by 1.

4. Apply heapify operation.

Have a look at the animation below to understand it better:

![Delete Operation](https://i.imgur.com/BHbhMni.gif)

Implementation:

    public void deleteElement(int num){

        int i;
        // Search the index of num
        for(i = 0; i < size; i++)
            if(num == heap[i])
                break

        // Swap operation of the num with the last index of the heap
        int temp = heap[i];
        heap[i] = heap[size-1];
        heap[size-1] = temp;
        size = size - 1;

        // Apply heapify
        buildHeap(heap);

    }

**Time Complexity**: Searching an element will take *O(n)* time-complexity. Then one swap operation to swap that element with the last element. and Then again buildHeap operation which will take *O(n)* time-complexity. So, the overall time-complexity is ***O(n)***.
