Hello Readers,

Every one of you would have taken a ride on public transport buses🚌 or trains🚝. You might have observed that the person of old age is given priority over others.

![Public Transport](https://i.imgur.com/QQeCWil.jpeg)

Now let's say you have the responsibility of distribution of seats among people based on age which you already know, How will you do this task using programming?

> arrayOfAge = [9,4,6,8,5]

> numberOfSeats = 3

Alright, you might have guessed it correctly. Just Sort the array and pick 3 people with a maximum age.

--------------

📝What's the time complexity of this approach? 

🎯***O(n.log(n))***

--------------------------------------------------------------------------------------
But, Let's say there are m stops for the bus and at each stop, one person acquiring the seat leaves and another person enters the bus. To whom do you allot the seat? Will you do sorting again and again for each stop and allow the seat to the person with maximum age? Let's first analyze this approach...

Sorting for each stop will take ***O(n.log(n))*** time and doing it m times. So, the total time complexity will be ***O(m.n.log(n))***.

Now, We want to optimize the algorithm. Here comes our Data-Structure ***Priority-Queue or Heap***.

You might be wondering🤔, What's special in this data-structure?

The above algorithm could be solved in just ***O(m.log(n))***, Isn't it is much better than before😀?

Now Let's understand Priority Queue and how can it optimize our problem?

----------------------------------------------------------------------------------------------------------------------

# Priority Queue (HEAP)

In the priority queue, an element with the highest priority served first then the rest of the elements. Basically, the elements are arranged in this data-structure based on priority. Priority could be of any type eg. maximum value, minimum value, etc. 

-------------------------

📝Think🤔 about how can we prioritise people in the example above?

🎯Hoping you already got it, We can prioritize people based on age i.e. the person with the maximum age🧓 should be given a seat first.

--------------------------

<br>
Heap satisfies the following properties:

1. The tree of a heap is a complete binary tree i.e. Height is always ***O(logn)***.
2. Heap follows the order of elements internally. E.g. In a Max-Heap, a parent's value is greater than equal to that of its children.

---------
📝What is a complete binary tree?

🎯In a complete binary tree:

  - Every level is filled with nodes except the last.
  - Nodes are aligned from left to right.
  - So, the maximum height is log(N).
  
------------

#### Illustration of MAX-HEAP


<div style="display:flex;">
<img src="https://i.imgur.com/eI7kJgc.jpg" alt="drawing" width="400" height="250"/>
<br>
<img src="https://i.imgur.com/ZFWgiMz.jpg" alt="drawing" width="450" height="60"/>
</div>


In heap, the children of an element at index **'i'** are at positions (2*i + 1) and (2*i + 2) as its binary tree is completely balanced. 

<br>
Now, Let's have a look at the operations of the heap:

1. ***buildHeap***: From a given array, We can build a heap in *O(n)* time complexity.
2. ***insert***: Addition of an element to heap could be done in *O(logn)* time complexity.
3. ***pop***: Removes an element with the highest priority from the heap in *O(logn)* time complexity.
4. ***seek***: Returns highest priority element from the heap in *O(logn)* time complexity.
5. ***isEmpty***: Checks if the heap consists of any element in *O(1)* time complexity.
6. ***size***: Returns the count of the number of elements in heap in *O(1)* time complexity.
7. ***heapify***: Orders the heap on the index that violates the heap property in *O(logn)* time complexity.
8. ***deleteElement***: Removes the element from the heap in *O(n)* time complexity.

<br>
Now, Let's build a heap. 

![Build Heap](https://upload.wikimedia.org/wikipedia/commons/4/4d/Heapsort-example.gif)


Let's declare🛠 the structure of the heap keeping in mind the operations of the heap.

    public class Heap{

        private int size; // Number of elements in heap
        private int[] heap; // Heap array

        public Heap(int heapSize){
            heap = new int[heapSize];
            size = 0;
        }

        public void buildHeap(int[] arr){
            // discussed below
        }

        public boolean isEmpty(){
            return (size == 0);
        }

        public int size(){
            return size;
        }

        public int seek(){
            if(isEmpty()){
                throw new IllegalStateException();
            }
            return heap[0];
        }

        public void insert(int element){
            // discussed below
        }

        public int pop(){
            // discussed below
        }
        
        private void heapify(int index){
            // discussed below
        }
        
    }


## HEAP OPERATIONS

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

--------

- #### Heapify

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

---------

- #### Inserting an element into the heap

Add element into a heap at the end and maintain order using heapify operation.

![Insertion Operation](https://i.imgur.com/7hOLrl9.gif)

    public void insert(int element){
        // increment size to add new element
        size = size + 1;
        heap[size-1] = element; // heap Array follows zero'th index
        
        // Arrange the elements to follow heap property
        for(int i = (size/2); i >= 0; i--)
            heapify(i);
    }
    
--------------------

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
    
 ---------------
    
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
        for(int j = (size/2); j >= 0; j--)
            heapify(j);

    }

---------------------------------------
    
Now, Let's get back to our example discussed at the starting of the blog.

The notion of that example is that at each stop the passenger of the highest age leaves the bus and the new passenger enters. So, At each stop, we have to allow the seat to the passenger with a maximum age.

So, how heap improves our algorithm🙄?

We can pop(leaving the bus) the passenger 🧍‍ from the heap in O(logn) time complexity and insert the new passenger in O(logn) time-complexity. So the *Overall time-complexity of our algorithm will be **O(m.log(n))***.

Hope you understood the heap and its operations🏆.

Thanks for reading.😊
