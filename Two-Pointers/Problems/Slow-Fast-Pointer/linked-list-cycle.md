# [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

- Given head, the head of a linked list, determine if the linked list has a cycle in it.

- There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. 
- Internally, pos is used to denote the index of the node that tail's next pointer is connected to. 
- Note that pos is not passed as a parameter.

- Return true if there is a cycle in the linked list. Otherwise, return false.

### Input: 
    head = [3,2,0,-4], pos = 1
### Output: 
    true
### Explanation: 
    There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
    
![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)
    
------------------------------------------------------------------------------

## Solution

- Two Pointers
  - Use Two-Pointers ***slow*** and ***fast***.
  - Move ***slow*** by one step.
  - Move ***fast*** by two step.
  - If slow and fast meet at a point, Then there exists a cycle.
  
-----------------------

### Python Code

    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, x):
    #         self.val = x
    #         self.next = None

    class Solution:
        def hasCycle(self, head: ListNode) -> bool:

            slow,fast = head,head

            while(fast != None and fast.next != None):
                slow = slow.next
                fast = fast.next.next
                if(slow == fast):
                    return True

            return False
            
---------------------------------------------------


🎯 What is the time complexity of the above solution?

📝 ***O(N)***

    As we are considering each node only once using slow pointer and in worst case twice by fast pointer.
