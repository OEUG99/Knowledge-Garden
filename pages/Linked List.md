title:: Linked List
tags:: [[Data Structures and Algorithms]]

- # What is a linked list?
	- A linked list is a common data structure used in computer programming to store a collection of elements, or nodes, in a linear sequences.
	- In a linked list, each node contains two parts:
		- 1. the data (which represents the value of the node)
		  2. the pointer (which points to the next node in the sequence)
	- The nodes in a linked list are not necessarily stored in order in memory, as in the case of a regular list/array. Instead, each node in the list is stored in a separate memory location, and the pointer points to the next nodes location.
	- This allows for dynamic allocation and efficient insertion and deletion of elements, since new nodes can be added or removed from the sequence simply by adjusting the pointers in the adjacent nodes.
	- However, accessing a specific element in a linked list can be slower than in an array, since elements are not stored in continuous manner.
	- ## Types of linked lists
	  heading:: 2
		- **Single Linked List:** Navigation is forward only.
		- **Doubly Linked List:** Forward and backward navigation is possible.
		- **Circular Linked List:** Last element is linked to the first element.
	- ## Example Code
	  heading:: 2
		- ```python
		  class Node:
		    def __init__(self, data):
		        self.data = data
		        self.next = None
		  
		  class LinkedList:
		    def __init__(self):
		        self.head = None
		  
		    def add_node(self, data):
		        new_node = Node(data)
		        if self.head is None:
		            self.head = new_node
		        else:
		            current = self.head
		            while current.next is not None:
		                current = current.next
		            current.next = new_node
		  
		    def print_list(self):
		        current = self.head
		        while current is not None:
		            print(current.data, end=' -> ')
		            current = current.next
		        print('None')
		  
		  ```
- # Below needs to be corrected
	- ((65344344-53f7-4876-9000-8f394d5114ff))
	- #[[Linked List]]
	  id:: 65307641-ef2b-4d75-8c60-5698c47c2f54
	  collapsed:: true
		- ## Insertion
		  id:: 65344344-53f7-4876-9000-8f394d5114ff
			- Unlike traditional #arrays, linked lists are efficient at inserting into the start of series of numbers. An array insertion at index 0 is O(N) due to it having to shift everything to the right, where as a linked list is O(1) as it only has to adjust the pointers.
			- insertion anywhere in a linked list is O(1)
		- ## Deletion
			- to delete a node from the beginning of a linked list, we just change the first node of the linked list to point to the second.
			- this can be done in 1 step.
			- to delete a node at the end of a linked list, we just update the second to last node to point to null.
			- | Situation | Array | Linked List |
			  | --- | --- | --- |
			  | Delete at beginning | Worst case | Best case |
			  | Delete at middle | Average case | Average case |
			  | Delete at end | Best case | Worst case |
			- deleting anywhere besides the beggining and end can be complicated. We need to save the node the one we wish to delete and the one after. We delete the node we wish to remove, then update the first saved node to point to the second saved node.
		- ## Efficiency of Linked List Operations
			- | Operation | Array | Linked List |
			  | --- | --- | --- |
			  | Reading | O(1) | O(N) |
			  | Search | O(N) | O(N) |
			  | Insertion | O(N), but O(1) if at end. | O(N), but O(1) at beginning. |
			  | Deletion | O(N), but O(1) if at end. | O(N), but O(1) at beginning. |