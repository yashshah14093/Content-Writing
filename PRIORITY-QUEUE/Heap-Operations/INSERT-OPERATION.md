# INSERT OPERATION

- #### Inserting an element into the heap

Add element into a heap at the end and maintain order using heapify operation.

![Insertion Operation](https://i.imgur.com/7hOLrl9.gif)

    public void insert(int element){
        // increment size to add new element
        size = size + 1;
        heap[size-1] = element; // heap Array follows zero'th index
        
        int child = size-1;
        int parent;
        // Arrange the elements to follow heap property
        while(child > 0){
            parent = (child-1)/2;
            heapify(parent);
            child = parent;
        }
    }
    
**Time-Complexity**: In this operation, we need to compare elements from the leaf till root of the tree which is equal to the height of the tree. Therefore the time-complexity is O(height) = ***O(log(n))***.
