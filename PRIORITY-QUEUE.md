Hello Readers,

Everyone of you would have taken a ride in public transport buses🚌 or trains🚝. You might have observed that the person of old age are given priority over others.

![Public Transport](https://i.imgur.com/QQeCWil.jpeg)

Now let's say you have the responsibility of distribution of seats among people based on age which you already know, How will you do this task using programming?

> arrayOfAge = [9,4,6,8,5]

> numberOfSeats = 3

Alright, you might have guessed it correctly. Just Sort the array and pick 3 people with maximum age.

--------------

📝What's the time complexity of this approach? 

🎯***O(n.log(n))***

--------------------------------------------------------------------------------------
But, Let's say there are m stops for the bus and at each stop one people acquiring the seat leaves and another person enteres the bus. To whom do you allot the seat? Will you do sorting again and again for each stop and allot the seat to the person with maximum age? Let's first analyze this approach...

Sorting for each stop will take ***O(n.log(n))*** time and doing it m times. So, the total time-complexity will be ***O(m.n.log(n))***.

Now, We want to optimize the algorithm. Here comes our Data-Structure ***Priority-Queue or Heap***.

You might be wondering🤔, What's special in this data-structure?

The above algorithm could be solved in just ***O(m.log(n))***, Isn't it is much better than before😀?

Now Let's understand Priority Queue and how can it optimise our problem?

----------------------------------------------------------------------------------------------------------------------

# Priority Queue (HEAP)

In priority queue, an element with the highest priority served first than the rest of the elements. Basically, the elements are arranged in this data-structure based on priority. Priority could be of any type eg. maximum value, minimum value etc. 

-------------------------

📝Think🤔 about how can we prioritise people in the example above?

🎯Hoping you already got it, We can prioritise people based on age i.e. the person with the maximum age🧓 should be given seat first.

--------------------------

<br>
Heap satisfies the following properties:

1. Tree of a heap is a complete binary tree i.e. Height is always ***O(logn)***.
2. Heap follows the order of elements internally. E.g. In a Max-Heap, parent's value is greater than equal to that of its children.

#### Illustration of MAX-HEAP

![Heap Tree](https://i.imgur.com/miuYCb9.jpg)

![Heap Array](https://i.imgur.com/tPerrgl.jpg)

In heap, the children of an element at index **'i'** are at positions (2*i + 1) and (2*i + 2) as its binary tree is completely balanced. 

<br>
Now, Let's have a look at the operations of heap:

1. ***buildHeap***: From a given array, We can build a heap in *O(n)* time-complexity.
2. ***insert***: Addition of an element to heap could be done in *O(logn)* time-complexity.
3. ***pop***: Removes an element with highest priority from the heap in *O(logn)* time-complexity.
4. ***seek***: Returns highest priority element from heap in *O(logn)* time-complexity.
5. ***isEmpty***: Checks if the heap consists of any element in *O(1)* time-complexity.
6. ***size***: Returns the count of number of elements in heap in *O(1)* time-complexity.

<br>
Now, Let's build a heap. 

![Build Heap](https://upload.wikimedia.org/wikipedia/commons/4/4d/Heapsort-example.gif)


Let's declare🛠 the structure of heap keeping in mind the operations of heap.

    public class Heap{

        private int size; // Number of elements in heap
        private int[] heap; // Heap array

        public Heap(int heapSize){
            heap = new int[heapSize];
            size = 0;
        }

        public int buildHeap(int[] arr){
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

        private void slideUp(int childIndex){
            // discussed below
        }
    }

-------------
📝Now Let's say you have an array of length n and you want to build a heap from its elements. So, which function you need to implement?

🎯Hoping, you got this correctly. We need to pass the array as a parameter into buildHeap function to construct🔨 a heap. 

--------------
Let's implement it.

    public buildHeap(int[] arr){
        size = arr.length;

        // Copy elements of arr into heap array
        for(int index = 0; index < size; index++)
            heap[index] = arr[index];

        // Arrange the elements based on Max-Heap property
        for(int i = 0; i < size; i++)
            slideUp(i); // discussed below

    }

----------
- #### slideUp

If you observe the animation and code above, you will understand that after insertion of an element in the heap, You need to maintian the heap order property. If the value of children is greater than (>) its parent, then we need to swap⇆ that element with its parent. For this we can use the code💻 of ***'slideUp'*** mentioned below.


     private void slideUp(int child){
      
        int parent = (child-1)/2;

        int temp;

        if(parent < 0){
            return;
        }

        if(heap[parent] < heap[child]){
            temp = heap[parent];
            heap[parent] = heap[child];
            heap[child] = temp;
            slideUp(parent);
        }
    }
    
---------

Let's implement other operations also.

- #### Inserting an element into heap

Add element into heap at the end and maintain order using slideUp operation.

    public void insert(int element){
        // increment size to add new element
        size = size + 1;
        heap[size-1] = element; // heap Array follows zero'th index
        slideUp(size-1);
    }
    

- #### Removing maximum element from the heap i.e. *'pop' operation*

📝Which element is of highest priority in heap?

🎯Definitely, The element at index 0. 

So, we just need to remove that element and again maintaining an order.

But Again which operation we need to use to maintain the order.

Is it slideUp? Yes you can use it but is it feasible for this operation? Actually No, In slideUp operation you need to use it for each element but the element out of order is only at index 0. We can improve the performance by only maintaining the order of the element of index 0 for which we can use slideDown operation which will be discussed in detail after the pop operation.

    public int pop(){
        if(isEmpty())
            throw new IllegalStateException();

        int value = heap[0];
        heap[0] = heap[size-1];
        size = size - 1;
        slideDown(0); // discussed below
        return value;
    }
    
 
 - #### Slide Down
 
 In the slideUp operation, we compare the child element with the parent's value. But here we need to do just the opposite of it. 
 
 First focus on which index we need to apply the slideDown operation.
 
 The parent's index which is not following heap order property with its child's index. This could be solved by swapping⇆ parent element with the maximum value among the child elements.
 
 Have a look at the implementation below.
 
     private void slideDown(int parent){
        int leftChild = 2*parent + 1;
        int rightChild = 2*parent + 2;
        int childIndex = null;
        int temp;

        if(leftChild < size)
            childIndex = leftChild;

        if(rightChild < size && heap[leftChild] < heap[rightChild])
            childIndex = rightChild;

        if(childIndex && heap[parent] < heap[childIndex]){
            temp = heap[parent];
            heap[parent] = heap[childIndex];
            heap[childIndex] = temp;
            slideDown(childIndex);
        }

    }
 
 ------------
    
Now, Let's get back to our example discussed in the starting of the blog.

The notion of that example is that at each stop the passenger of highest age leaves the bus and the new passenger enteres. So, At each stop we have to allot the seat to the passenger with maximum age.

So, how heap improves our algorithm🙄?

We can pop(leaveing the bus) the passenger 🧍‍ from the heap in O(logn) time-complexity and insert the new passenger in O(logn) time-complexity. So the *Overall time-complexity of our algorithm will be **O(m.log(n))***.

Hope you understood the heap and its operations🏆.

Thanks for reading.😊
