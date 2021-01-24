# Pointer-1 and Pointer-2 from Two Sequences

- In each sequence, we will use one pointer to loop it. 

- Each pointer represents the current logical position in the corresponding sequence. 

- At each step we will compare currently indexed element, and process logic between them.


![](https://i.imgur.com/7DuNmnb.jpg)

### Example

## Merge Two Sorted Arrays 

> Given two sorted integer arrays ***arr1*** and ***arr2***. Return one sorted array by merging ***arr1*** and ***arr2***.

### Input:

*arr1 = [1,2,3]*

*arr2 = [2,5,6]*

### Output:

*[1,2,2,3,5,6]*

## Solution:

    public class Main {

        public static void merge(int[] arr1,int n,int[] arr2,int m,int[] result){

            // one and two are pointers to traverse on arr1 and arr2 arrays
            // k pointer to traverse the result array to store result
            int one = 0, two = 0,k = 0;

            // loop until we finish one of the two arrays
            while(one < n && two < m){
                // insert integer which is less between the two
                // and increase their respective pointers
                if(arr1[one] <= arr2[two]){
                    result[k] = arr1[one];
                    one = one + 1;
                }else{
                    result[k] = arr2[two];
                    two = two + 1;
                }
                // increase pointer for result array
                k = k + 1;
            }

            // if arr1 is left traversed then copy its remaining elements
            if (one < n) 
                for (int i=one; i<n; i++) {
                    result[k] = arr1[i];
                    k++;
                }

            // if arr2 is left traversed then copy its remaining elements
            if (two < n) 
                for (int i=two; i<m; i++) {
                    result[k] = arr2[i];
                    k++;
                }

        }


        public static void main(String[] args) {

            int[] arr1 = {1,2,3}, arr2 = {2,5,6};
            int n = arr1.length, m = arr2.length;

            // this array will store result
            int[] result = new int[n+m];

            merge(arr1,n,arr2,m,result);

            // output of result array
            for(int index = 0; index < n+m; index++)
                System.out.print(result[index]+" ");
        }
    }
