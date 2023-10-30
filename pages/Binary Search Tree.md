# Summary
heading:: 1
	- A binary search tree is a tree that has zero, one, or tow children.
	- A binary search tree must also abide by the following rules:
		- each node can have *at most* one "left" and one "right" child.
		  logseq.order-list-type:: number
		- A node's "left" descendants can only contain values that are less than the node itself. Likewise, a node's "right" descendants can only contain values that are greater than the node itself.
		  logseq.order-list-type:: number
	- An example of a binary tree that is **not** a binary search tree:
	- {{renderer code_diagram,mermaid}}
		- ```mermaid
		  graph LR
		  
		  50 --- 20
		  50 --- 30
		  ```
	- ## What use cases do binary search trees excel at?
	  heading:: 2
		- If you want a data structure that maintains order yet also has fast search, fast insertion, and fast deletion, then binary search trees are the data structure that you need.
	-