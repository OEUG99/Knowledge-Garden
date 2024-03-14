tags:: [[Programming]]

- # Introduction to FS (File System)
  heading:: 1
	- url:: https://www.geeksforgeeks.org/node-js-file-system/
	  archive:: https://archive.is/hChZB
	- ## What is the FS Module?
	  heading:: 2
		- To handle file operations like creating, reading, deleting, etc., Node.JS provides an inbuilt module called FS (File System).
	- ## Synchronous vs Asyncronous approaches
	  heading:: 2
		- **Synchronous approach:** They are called blocking funcitons as it waits for each operation to complete, only after that, it executes the next operation.
		- **Asynchronous approach:** They are called non-blocking functions as it never waits for each operation to complete, rather it executes all operations in the first go itself.
	- ### When should you use these different approaches?
	  heading:: 3
		- If your operations are not doing very heavy lifting like querying huge data from DB then go ahead with Synchronous way, otherwise async.
		- In an async way, you can show some progress indicator the user while in the background, you can continue with your heavyweight work. This is ideal for scenario for GUI based apps.
	- ## How to read
	  heading:: 2
		- ```
		  fs.readFile()
		  
		  fs.readFileSync()
		  ```
	- ## How to open
	  heading:: 2
		- ```
		  fs.open(path, flags, mode callback)
		  ```
			- **path:** It holds the name of the file to read or the entire path if stored at other locations.
			- **flags:** Flags indicate the behavior of the file to be opened. All possible values are ( r, r+, rs, rs+, w, wx, w+, wx+, a, ax, a+, ax+).
			- **mode:** Sets the mode of file i.e. r-read, w-write, r+ -readwrite. It sets to default as readwrite.
	-