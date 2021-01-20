# POP OPERATION

- #### Removing a maximum element from the heap i.e. *'pop' operation*

📝Which element is of the highest priority in the heap?

🎯Definitely, The element at index 0. 

So, we just need to remove that element and again maintaining an order.

But Again which operations we need to use to maintain the order.

First of all swap the element at index 0 with the last index. and Then use heapify to again reorder the elements at index 0.

Return the element of last index and then decrease the size of heap.

![Pop Operation](https://i.imgur.com/x5nSkP5.gif)

Implementation:

    public int pop(){
        if(isEmpty())
            throw new IllegalStateException();

        int value = heap[0];
        heap[0] = heap[size-1];
        size = size - 1;
        heapify(0);
        return value;
    }
    
**Time-Complexity**: In this operation, we are performing just one swap operation and a heapify operation at the root of the tree. Thus, the time-complexity of this operation is same as that of heapify operation that is: ***O(log(n))***.
