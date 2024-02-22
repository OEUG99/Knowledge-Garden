tags::  [[Programming]] [[Data Structures and Algorithms]] [[Leetcode]]
- # What is a Binary Tree?
  heading:: 1
	- Node at the top is called **root.**
	- In a tree, a node has pointers to its **children**.
	- What makes a binary tree "binary"?
		- In a binary tree, all nodes have a maximum of two children. These children are referred to as the **left** and **right** child.
	- ## Tree terminology
	  heading:: 2
		- **root** node is the top of the tree.
			- similar to the head of a linked list.
		- **depth** of a node is how far from the root node.
		- **subtree** of a tree is a node and all of its dependancies
			- trees are recursive, you can treat a subtree as if it was its own tree, with a chosen node being the root.
- # Traversing binary trees with DFS
  heading:: 1
	- DFS stands for Depth-first search.
	- For binary trees there are 3 ways to perform DFS:
		- 1. preorder
		  2. inorder
		  3. post order
	- In DFS we start at the root and prioritize depth by traversing as far down the tree as possible in one direction until reaching a leaf node)
		- Because we need to move back up the tree after reaching a leaf, DFS is typically implemented using recursion, although it is also sometimes done iterative using a stack
	- ### Example Code of DFS:
	  heading:: 3
		- ```python
		  def dfs(node):
		    if node == None:
		        return
		  
		    dfs(node.left)
		    dfs(node.right)
		  ```
		- In this example, for every node, it is searching the two subtrees of the child nodes.
	-