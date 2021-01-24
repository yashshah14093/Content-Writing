# Slow and Fast Runner

Imagine two racers🏃‍♀️ running in a circular racing track. If one racer is faster than the other, the faster racer is bound to catch up and cross the slower racer from behind. In each iteration, Tortoise :turtle: (slow pointer) moves one step and the Hare :rabbit2: (fast pointer) moves two steps.

![](https://i.imgur.com/fA6t2FP.jpg)

In the two pointer technique, We can refer one pointer as slow-runner(Tortoise🐢) and other as fast-runner(Hare🐇).

We can use this strategy to detect a cycle in the Linked-List.

If we discover a cycle we know a few things.

- The slow pointer and the fast pointer are at the same node.
- The fast pointer has traveled a further distance than the slow node.


      /**
       * Definition for singly-linked list.
       * class ListNode {
       *     int val;
       *     ListNode next;
       *     ListNode(int x) {
       *         val = x;
       *         next = null;
       *     }
       * }
       */
      public class Solution {
          public boolean hasCycle(ListNode head) {

              ListNode slow = head;
              ListNode fast = head;

              while(fast != null && fast.next != null){
                  slow = slow.next;
                  fast = fast.next.next;
                  if(slow == fast)
                      return true;
              }

              return false;
          }
      }
      
![](https://cdn.emre.me/2019-10-23-tortoise-and-hare.gif)
