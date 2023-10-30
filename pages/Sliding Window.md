category:: [[Data Structures and Algorithms]]
tags:: [[Programming]] [[Data Structures and Algorithms]] [[Two Pointers]] [[Leetcode]]

	- Sliding window is actually implemented using two pointers.
	- Subarrays are just a section of an array.
		- **Left bound** the starting index
		- **Right bound** the ending index.
	- The idea behind the sliding window technique is to efficiently find the "best" window that fits some constraint.
	- The general algorithm behind sliding windows is:
		- 1. Define a pointer for the left and right bound that represents he current window, usually both of them start at 0.
		  2. iterate over the array with the round bound to "add" elements into the window.
		  3. Whenever the constraint is broken, then "remove" elements from the window by increasing the left bound until the condition is satisfied again.
	- The big idea behind sliding windows is to avoid doing duplicate instructions, for example by shifting the sliding window, we just have to modify the previous windows sum by removing the previous initial element, and then adding into the new ending element. https://youtu.be/GcW4mgmgSbw
	-