# BUILDING A HEAP

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
