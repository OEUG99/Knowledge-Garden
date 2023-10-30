title:: Linked List
tags:: [[Programming]] [[Data Structures and Algorithms]] [[Leetcode]]

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