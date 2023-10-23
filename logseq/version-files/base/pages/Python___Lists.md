# What are lists?
heading:: 1
	- Lists are an unordered mutable collection of objects, which means that its elements can be modified after creating the list.
	- Lists are created using the square brackets `[]` and each element is separated by commas.
		- Example:
			- ```python
			  exampleList = [1,2,3,4]
			  ```
- # Methods for Lists:
  heading:: 1
	- `append()` – adds an element to the endo f the list
	- `insert()` – adds an element at the specified index
		- example: `exampleList.insert(0,"a")` to insert "a" into the 1st element.
	- `reverse()` – reverses the order of the elements in the list.
	- `remove()` – removes the first occurrence of a specified value from the list.
		- example: `exampleList.remove("a")` to remove the first "a" in the list.
	- `pop()` – removes and return the element at the specified position in the list.
	- `clear()` – removes all elements from the list.
	- `sort()` – sorts the entire list alpha-numerically using [[Algorithm/TimSort]]
		- You can also have the parameter `reverse=True` to reverse the sorting order.
			- example: `exampleList.sort(reverse=True)`