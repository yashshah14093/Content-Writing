# Left and Right Boundary

In this technique, One pointer starts from the beginning, while the other pointer starts from the end. They move toward each other until they meet in the middle.

![Picture](https://i.imgur.com/GivGQvI.png)

The condition to stop the scanning of whole array is left >= right.

### Example:

## Binary Search

Finding the target by reducing the lower and upper bounds continuously by maintaining two pointers:
- low -> lower bound
- high -> higher bound

![1](https://i.imgur.com/Zvrqyaj.png)


    public class Main {

        public static boolean binarySearch(int[] arr,int target){
            int low,high,mid;
            low = 0;
            high = arr.length;

            while(low < high){
                mid = low + (high - low + 1)/2;
                if(arr[mid] == target)
                    return true;
                else if(arr[mid] < target)
                    high = high - 1;
                else
                    low = low + 1;
            }

            return false;
        }


        public static void main(String[] args) {
            int[] arr = {9,7,6,4,3,2,1};
            int target = 6;
            if(binarySearch(arr,target))
                System.out.println("Found");
            else
                System.out.println("Not Found");
        }
    }
