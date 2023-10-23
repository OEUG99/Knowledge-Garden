category:: [[Programming]]

- # What is a handle in C++
  heading:: 1
	- A handle is an abstract reference to a resource that is used when application software references blocks of memory or objects that are managed by another system like a database or operating system.
	- https://stackoverflow.com/questions/1303123/what-is-a-handle-in-c
- # Templates in C++
  heading:: 1
  id:: 63463386-9a1d-4c8b-a6a9-b9154dc8f51c
	- Templates are the foundation of [[Generic Programming]] , which involves writing code in a way that is independent of any particular type.
	- A template is a blueprint or formula for creating a generic class or function.
		- The libraries like  _containers, iterators, algorithms_ are examples of generic programming and have been developed using template concept.
	- There is a single definition of each container, such as **vector**, but we can define many different kings of vectors for example, **vector<int>** or **vector<string>**
	- you can use templates to define functions as well as classes, let us see how they work:
	- ## Function Tempalte:
	  heading:: 2
		- The general form of a template funciton definition is shown here:
			- ```C++
			  template <class type> ret-type func-name(parameter list) {
			   // body of function
			  } 
			  ```
				- In the above example, _type_ is a palceholder name for a data type used by the function. This name can be used within the function definition.
				- The following is the example of a function template that returns the maximum of two values:
					- ```C++
					  #include <iostream>
					  #include <string>
					  
					  using namespace std;
					  
					  template <typename T>
					  inline T const& Max (T const& a, T const& b) { 
					   return a < b ? b:a; 
					  // for this return statement: [conditional statement ] -> if true then b if false then a
					  // that is what the question mark does.
					  }
					  
					  int main () {
					   int i = 39;
					   int j = 20;
					   cout << "Max(i, j): " << Max(i, j) << endl; 
					  
					   double f1 = 13.5; 
					   double f2 = 20.7; 
					   cout << "Max(f1, f2): " << Max(f1, f2) << endl; 
					  
					   string s1 = "Hello"; 
					   string s2 = "World"; 
					   cout << "Max(s1, s2): " << Max(s1, s2) << endl; 
					  
					   return 0;
					  }
					  ```
					- If we compile the above code and run we get:
						- ```
						  Max(i, j): 39
						  Max(f1, f2): 20.7
						  Max(s1, s2): World
						  ```
		- ## Class Template:
		  heading:: 2
			- Just as we can define function templates, we can also define class templates. The general form of a generic class declaration is shown here:
				- ```C++
				  ```
					- In the above example, **type** is the placeholder type name, which will be specified when a class is instantiated. You can define more then one generic data type by using a comma seperated list.
					- The following is an example to define class _stack<>_ and implement generic methods to push and pop the elements from the stack:
						- ```C++
						  #include <iostream>
						  #include <vector>
						  #include <cstdlib>
						  #include <string>
						  #include <stdexcept>
						  
						  using namespace std;
						  
						  template <class T>
						  class Stack { 
						   private: 
						      vector<T> elems;    // elements 
						  
						   public: 
						      void push(T const&);  // push element 
						      void pop();               // pop element 
						      T top() const;            // return top element 
						      
						      bool empty() const {      // return true if empty.
						         return elems.empty(); 
						      } 
						  }; 
						  
						  template <class T>
						  void Stack<T>::push (T const& elem) { 
						   // append copy of passed element 
						   elems.push_back(elem);    
						  } 
						  
						  template <class T>
						  void Stack<T>::pop () { 
						   if (elems.empty()) { 
						      throw out_of_range("Stack<>::pop(): empty stack"); 
						   }
						   
						   // remove last element 
						   elems.pop_back();         
						  } 
						  
						  template <class T>
						  T Stack<T>::top () const { 
						   if (elems.empty()) { 
						      throw out_of_range("Stack<>::top(): empty stack"); 
						   }
						   
						   // return copy of last element 
						   return elems.back();      
						  } 
						  
						  int main() { 
						   try {
						      Stack<int>         intStack;  // stack of ints 
						      Stack<string> stringStack;    // stack of strings 
						  
						      // manipulate int stack 
						      intStack.push(7); 
						      cout << intStack.top() <<endl; 
						  
						      // manipulate string stack 
						      stringStack.push("hello"); 
						      cout << stringStack.top() << std::endl; 
						      stringStack.pop(); 
						      stringStack.pop(); 
						   } catch (exception const& ex) { 
						      cerr << "Exception: " << ex.what() <<endl; 
						      return -1;
						   } 
						  } 
						  ```
							- If we compile the above code and run, this would produce the following results:
								- ```
								  Exception: Stack<>::pop(): empty stack
								  ```