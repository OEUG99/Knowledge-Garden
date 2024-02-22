tags:: [[Programming]] [[Website Development]]
- The Model-View-Controller (MVC) is an architectural pattern that separates an application into three main logical components:
  1. The **Model**
  2. The **View**
  3. The **Control**
- Each of these components are built to handle specific developmental aspects of an application. MVC is one of the most frequently used industry-standard web development frameworks to create scalable and extensible projects.
- # The Model:
	- The model component corresponds to all data- related logic that the user works with. This can represent the data that is being transferred between the View and Controller components or any other business logic-related data.
		- For example, a Customer object will retrieve the customer information from the database, manipulate it and update its data back to the database or use it to render data.
- # The View:
	- The View component is used for all the UI logic of the application.
		- For example, the Customer view will include all the UI components such as text boxes, drop-downs, etc, that the final user interacts with.
- # The Control:
	- Controller/Control acts as an interface between Model and View components to process all the business logic and incoming requests, manipulates data using the model component and interact with the Views to render the final output. For example, the Customer controller will handle all the interactions and inputs from the Customer View and update teh database using Customer Model. The same controller will be used to view the Customer data.
- More info: https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller
- # MVC in Human Talk:
  heading:: 1
	- The **Model** is your core application. Everything your application can do is the model.
	- The **View** is there to visualize what's going on and provide a user interface.
	- The **Controller** is the glue needed to react to events and instruct the model and view what to do.