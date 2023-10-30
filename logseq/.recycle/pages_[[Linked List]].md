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