- ```python
  # Definition for singly-linked list.
  # class ListNode:
  #     def __init__(self, val=0, next=None):
  #         self.val = val
  #         self.next = next
  class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        prev = None
        curr = head
  
        while curr is not None:
            # getting hte next node 
            nextNode = curr.next
  
            #Now we gotta change where the previous node is point too aka reverse it.
            #Aka we change it's curr.next pointer to previous
            curr.next = prev
  
            # then we make the previous the current node, as we are about to swap to the next node
            prev = curr
  
            # we then swapp to the next node.
            curr = nextNode
  
        
        return prev 
  ```
-