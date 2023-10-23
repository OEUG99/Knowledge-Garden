topic:: [[Leetcode]]
pattern:: [[Dummy Node]]
theme:: [[DSA/Linked List]]
source-url:: https://leetcode.com/problems/merge-two-sorted-lists/

- # Code:
  heading:: 1
	- ```python
	  # Definition for singly-linked list.
	  # class ListNode:
	  #     def __init__(self, val=0, next=None):
	  #         self.val = val
	  #         self.next = next
	  class Solution:
	    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
	        
	        # We will use a dummy head, this makes it easier to construct an output.
	        # we will ignore the first node once we sorted the two others.
	        dummy = ListNode(0)
	        # current will act as an output, basically we will scan both lists at the same time, 
	        # compare each node and then add to this output to build a sorted linked list.
	        current = dummy
	  
	        # while both lists are not empty
	        while list1 and list2:
	  
	            # determing the order to insert into output list
	            if list1.val < list2.val:
	                current.next = list1
	                list1 = list1.next
	            else:
	                current.next = list2
	                list2 = list2.next
	            
	            current = current.next
	        
	  
	        # In cases where one list ends up being longer, we will add on the remaining list
	        # this only works because it is sorted.
	        # also, if empty list is provided, this will add the non empty to out output
	        current.next = list1 or list2
	  
	        # remember we added a dummy node to make it easier to construct an output linked list
	        # so by returning dummy.next we are basically ignoring the first node which we added
	        return dummy.next
	  ```
-