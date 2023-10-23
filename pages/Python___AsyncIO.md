- Python’s asyncio is a co-routine-based concurrency model that provides elegant constructs to write concurrent python code without using threads.
- # The basics of AsyncIO
  source:: https://medium.com/dev-bits/a-minimalistic-guide-for-understanding-asyncio-in-python-52c436c244ea
  archive-url:: https://archive.ph/80JfU
  heading:: 1
	- ## Intro to co-routines and async keyword
	  heading:: 2
		- In traditional python, a programmer makes functions to process input values. Similarly, in asyncio, one needs to create unique functions called **co-routines**
			- To do so we use the `async` keyword
			  collapsed:: true
				- example:
				  ```python
				  # A normal function
				  def add(x: int, y: int):
				  return x + y
				  
				  # A co-routine
				  async def add(x: int, y: int):
				  return x + y
				  ```
			- When we use the `async` keyword event loop can execute this particular function as a co-routine.
			  collapsed:: true
				- Example:
				  ```python
				  import asyncio
				  
				  # A co-routine
				  async def add(x: int, y: int):
				  return x + y
				  
				  # An event loop
				  loop = asyncio.get_event_loop()
				  
				  # Pass the co-routine to the loop
				  result = loop.run_until_complete(add(3, 4))
				  print(result) # Prints 7
				  ```
					- The method _run_until_complete_ means three things implicitly:
						- 1.  Start the loop
						- 2.  Execute co-routine passed as an argument
						- 3.  Stop the loop
					- The _run_until_complete_ method returns the value from co-routine completion_._ It is a simple example of creating a co-routine and scheduling it on an event loop.
						- ![CleanShot 2023-10-18 at 18.18.10@2x.png](../assets/CleanShot_2023-10-18_at_18.18.10@2x_1697667494908_0.png)
						- This way via run_until_complete is very similar to sync programming.
	- ## Scheduling multiple co-routines (in same loop)
	  heading:: 2
		- What if we need to schedule multiple co-routines on the same event loop as a batch asynchronously? We can do it like this:
			- ```python
			  import asyncio
			  
			  # A co-routine
			  async def add(x: int, y: int):
			    return x + y
			  
			  # An event loop
			  loop = asyncio.get_event_loop()
			  
			  # Create a function to schedule co-routines on the event loop
			  # then print results and stop the loop
			  async def get_results():
			    result1 = await add(3, 4)
			    result2 = await add(5, 5)
			  
			    print(result1, result2) # Prints 7 10
			    loop.stop()
			  
			  loop.create_task(get_results())
			  
			  # Blocking call interrupted by loop.stop()
			  try:
			    loop.run_forever()
			  finally:
			    loop.close()
			  ```
			- ![CleanShot 2023-10-18 at 18.37.31@2x.png](../assets/CleanShot_2023-10-18_at_18.37.31@2x_1697668668189_0.png)
	- ## Scheduling co-routines dynamically (in one go)
	  heading:: 2
		- What if we have to create co-routines at run-time dynamically? The most important construct to do that is `asyncio.gather` method.
		- Let us say we have ’n’ number of inputs, and we need to process them concurrently and get back results; asyncio.gather is the default way to go.
			- ```python
			  import asyncio
			  
			  # A co-routine
			  async def add(x: int, y: int):
			    return x + y
			  
			  # Create a function to schedule co-routines on the event loop
			  # then print results
			  async def get_results():
			    inputs = [(2,3), (4,5), (5,5), (7,2)]
			  
			    # Create a co-routine list
			    cors = [add(x,y) for x,y in inputs]
			    results = asyncio.gather(*cors)
			  
			    print(await results) # Prints [5, 9, 10, 9]
			  
			  asyncio.run(get_results())
			  ```
		- Notice the use of the [[Python/unpacking]] operator inside the `asyncio.gather` method.
	- ## Scheduling co-routines dynamically (as items are ready)
	  heading:: 2
		- Sometimes, you don’t want a waiter to bring all items at once, and you might want to consume one at a time as they are ready.
		- That can be achieved using `asyncio.as_completed` method. Instead of collecting all concurrent results in one go, we can now consume the earliest available result from scheduled co-routines.
		- Example:
			- ```python
			  import asyncio
			  
			  # A co-routine
			  async def add(x: int, y: int):
			    return x + y
			  
			  # Create a function to schedule co-routines on the event loop
			  # then print results
			  async def get_results():
			    inputs = [(2,3), (4,5), (5,5), (7,2)]
			    # Create a co-routine list
			    cors = [add(x,y) for x,y in inputs]
			  
			    # Prints results of co-routines as they are ready
			    # Beware of Non-deterministic ouput. The order can change based on
			    # which co-routine finishes first
			    for cor in asyncio.as_completed(cors):
			        print(await cor)
			  
			  
			  asyncio.run(get_results())
			  ```
	- ## Schedule co-routines with a time deadline
	  heading:: 2
		- Sometimes, one needs to schedule a co-routine but only wait for a certain amount of time and stop execution. That is where `asyncio.wait_for` method comes in handy.
		- The `asyncio.wait_for` method takes a co-routine or task with a timeout and raises an exception if the result is not ready within the timeout period.
			- Example:
			  ```python
			  import asyncio
			  import random
			  
			  # A co-routine
			  async def add(x: int, y: int):
			    # function can do work between 1 second to 5 seconds
			    await asyncio.sleep(random.randrange(1, 5))
			    return x + y
			  
			  # Create a function to schedule co-routines on the event loop
			  # then print results
			  async def get_results():
			    result = None
			    try:
			        # Wait for 3 seconds for co-routine to execute
			        result = await asyncio.wait_for(add(3, 4), timeout=3)
			    except asyncio.exceptions.TimeoutError:
			        result = "fallback payload"
			  
			    print(result)
			  
			  asyncio.run(get_results())
			  ```
	- ## Asyncio.gather() vs asyncio.as_completed() vs asyncio.run()
		- ### `asyncio.gather()`
		  heading:: 3
			- 1.  **Order of Results**: `asyncio.gather` waits for all the coroutines to complete and returns the results in the same order as the coroutines were passed.
			- 2.  **Error Handling**: By default, it waits for all coroutines to complete, even if some of them produce errors. It will then aggregate all exceptions and raise them. You can change this behavior with the `return_exceptions` parameter.
			- 3.  **Usage**:
				- ``` python
				    `result1, result2 = await asyncio.gather(coroutine1(), coroutine2())`
				  ```
			- 4.  **Blocking**: `asyncio.gather` blocks until all the passed coroutines are complete.
			- 5.  **Example**:
				- ```python
				  async def main():    
				  result1, result2 = await asyncio.gather(foo(), bar())`
				  ```
		- ### `asyncio.as_completed()`
		  heading:: 3
		  collapsed:: true
			- 1.  **Order of Results**: `asyncio.as_completed` returns an iterator that allows you to iterate over the results as they complete, without any concern for the order in which they were started.
			- 2.  **Error Handling**: If any coroutine produces an error, you will encounter it as soon as you try to access its result from the iterator.
			- 3.  **Usage**:
				- ```
				    pythonCopy code
				    `for coro in asyncio.as_completed([coroutine1(), coroutine2()]):     result = await coro`
				  ```
			- 4.  **Non-blocking**: You can start processing results as soon as the fastest coroutine is done. You don't have to wait for all of them to complete to start processing.
			- 5.  **Example**:
				- ```python
				  async def main():
				  for coro in asyncio.as_completed([foo(), bar()]):
				    	result = await coro         
				        print(f"Received result: {result}")`
				  ```
		- `asyncio.run()`
			- This is used as the main entry point for executing coroutines and does not return until the coroutine is done, effectively encapsulating the event loop. It creates a new event loop, runs the given coroutine, closes the loop, and finally returns the result. It's often used at the highest level to start the program.
			  logseq.order-list-type:: number
			- **Example:**
			  logseq.order-list-type:: number
			  ```python
			  async def hello():
			      print('Hello, World!')
			  
			  # Run a coroutine
			  asyncio.run(hello())
			  ```
			-
		- ### Summary
		  heading:: 3
			- `asyncio.gather()` is useful when you need to run multiple coroutines concurrently and wait for all of them to complete, possibly preserving their order.
			- `asyncio.as_completed()` is useful when you need to run multiple coroutines concurrently but want to start processing them as soon as each one is done, without waiting for all to complete, and without concern for their original order.
			- `asyncio.run()` is useful for being the mai entry point to run async code.