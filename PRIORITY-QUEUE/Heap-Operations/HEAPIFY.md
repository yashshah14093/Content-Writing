# HEAPIFY OPERATION

Heapify operation orders the heapArray at the given index to follow heap property.

To understand heapify operation on heap have a look at the animation below: 

![Heapify Operation](https://i.imgur.com/8azbFmG.gif)

      public heapify(int index){
          size = arr.length;
          int largest = index;
          int leftChild = 2*index+1;
          int rightChild = 2*index+2;

          if(leftChild < size && heap[leftChild] > heap[largest])
              largest = leftChild;
          if(rightChild < size && heap[rightChild] > heap[largest])
              largest = rightChild;

          if(largest != index){
              int temp = heap[largest];
              heap[largest] = heap[index];
              heap[index] = temp;
              heapify(largest);
          }
      }

**Time-Complexity**: To calculate time-complexity, We need to find the number of swap operation for the complete binary tree with N nodes. In the worst case the number of swap operations for a node is the height of its subtree which is *O(h)*. So, the time-complexity will ***O(log(n))*** for the heapify operation.
