title:: Design Patterns
category:: [[Programming]]

	- # Entity-Component-System #ecs #game-development
	  heading:: 1
		- An **Entity** is an ID.
		- A **Component** is a struct of data.
		- A **System** is the logic that operates on the components.
			- The important thing to know is how to implement these three in a way that is simple and easy to understand, and to use.
		- ## The Entity
		  heading:: 2
- # Model-View-Controller
  heading:: 1
  id:: 63484d07-5ec4-4cf3-ba9b-543f737a6909
	- # Model-View-Controller #mvc #web-development
	  heading:: 1
	- The Model-View-Controller (MVC) is an architectural pattern that separates an application into three main logical components:
	  1. The **Model**
	  2. The **View**
	  3. The **Control**
	- Each of these components are built to handle specific developmental aspects of an application. MVC is one of the most frequently used industry-standard web development frameworks to create scalable and extensible projects.
	- ## The Model:
	  heading:: 2
		- The model component corresponds to all data- related logic that the user works with. This can represent the data that is being transferred between the View and Controller components or any other business logic-related data.
			- For example, a Customer object will retrieve the customer information from the database, manipulate it and update its data back to the database or use it to render data.
	- ## The View:
	  heading:: 2
		- The View component is used for all the UI logic of the application.
			- For example, the Customer view will include all the UI components such as text boxes, drop-downs, etc, that the final user interacts with.
	- ## The Control:
	  heading:: 2
		- Controller/Control acts as an interface between Model and View components to process all the business logic and incoming requests, manipulates data using the model component and interact with the Views to render the final output. For example, the Customer controller will handle all the interactions and inputs from the Customer View and update teh database using Customer Model. The same controller will be used to view the Customer data.
	- More info: https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller
	- # MVC in Human Talk:
	  heading:: 1
		- The **Model** is your core application. Everything your application can do is the model.
		- The **View** is there to visualize what's going on and provide a user interface.
		- The **Controller** is the glue needed to react to events and instruct the model and view what to do.
- # How to select a design pattern
  heading:: 1
	- Consider how design patterns solve design problems.
	- Scan intent sections Each pattern has an intent
	- Study how patterns interrelate.
	- Study patterns of like purpose.
	- Examine a cause of redesign.
	- Consider what should be variable in your design.
- # How to use a Design Pattern
  heading:: 1
	- Read the pattern once through for an overview
	- Go back and study the Structure, Participants, and Collaborations sections.
	- Look at the Sample Code section to see a concrete example of the pattern in code.
	- Choose names for pattern participants that are meaningful in the application context.
	- Define the classes. Declare their instances, establish their inheritance relationships and define the instance variables that represent data and object references. Identify existing classes in your application that the pattern will affect and modify them accordingly.
	- define application specigic names for operations in the patterm.
		- you might use the "Create-" prefix to consistently denote a factory method.
	- Implement the operations to carry out the responsibility and collaborations in the pattern.