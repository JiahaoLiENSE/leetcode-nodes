### 141. Linked List Cycle

#### Description

`Given head, the head of a linked list, determine if the linked list has a cycle in it.`  
`There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.`  
`Return true if there is a cycle in the linked list. Otherwise, return false.`  

#### Example
![e1](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)  
Input: `head = [3,2,0,-4], pos = 1`  
Output: `true`  
Explanation: `There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).`  

![e2](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png)  
Input: `head = [1,2], pos = 0`  
Output: `true`  
Explanation: `There is a cycle in the linked list, where the tail connects to the 0th node.`  


#### Java
```java
```

#### Python
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: ListNode) -> bool:
        if head == None:
            return False
        slow = head
        fast = head.next
        while slow != None and fast != None and fast.next != None:
            if slow == fast:
                return True
            slow = slow.next
            fast = fast.next.next
        return False
```
