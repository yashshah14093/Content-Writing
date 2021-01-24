# Three Pointers

- Multiple pointers could be needed to keep track of states in the data-structure.
- Multiple pointers is nothing but just a variant of Two-Pointer Technique.
- Three Pointers can be applied to multiple problems including Dutch-National-Flag and 3SUM problem.

***3-WAY PARTITION***

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR0oRXocc0G1MNVPEKRMmfIpHYVE7De5S-Mkg&usqp=CAU)

### Example

## [Dutch National Flag Problem (3-way partition)](https://leetcode.com/problems/sort-colors/)

> Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.
We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.

#### Input: 
- nums = [2,0,2,1,1,0]
#### Output:
- [0,0,1,1,2,2]

## Solution 

We are classifying the array into four groups: red, white, unclassified, and blue. 

Initially we group all elements into unclassified. 

We iterate from the beginning as long as the white pointer is less than the blue pointer.

- If the white pointer is red (nums[white] == 0), we swap with the red pointer and move both white and red pointer forward.
- If the pointer is white (nums[white] == 1), the element is already in correct place, so we don't have to swap, just move the white pointer forward.
- If the white pointer is blue, we swap with the latest unclassified element.

      class Solution {

          public void sortColors(int[] nums) {

              int red = 0, white = 0, blue = nums.length-1;

              while(white <= blue){
                  if(nums[white] == 0){
                      swap(nums,red,white);
                      red += 1;
                      white += 1;
                  }
                  else if(nums[white] == 1)
                      white += 1;
                  else{
                      swap(nums,white,blue);
                      blue -= 1;
                  }

              }
          }

          private void swap(int[] arr, int one, int two){
              int temp = arr[one];
              arr[one] = arr[two];
              arr[two] = temp;
          }
      }
      

