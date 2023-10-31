# Pages
	- Page name should avoid abbreviation, i.e. `math` should be `mathematics.` This helps with avoiding name conflicts.
	- All pages should implement the `tags::` page prop. Each page should be tagged using the following method.
		- ## Tagging Pages
			- Create a list of tags inside the `tags::` page prop, start with something broad, then narrow it down and refine it.
				- **Example:**
					- ```
					  # lets assume our page is on World War 2 weapons.
					  tags:: [[History]], [[World War 2]], [[War]], [[Weapons]]
					  
					  # Now lets assume we are making a page for web development.
					  tags:: [[Programming]] [[Website Development]] [[HTML]]
					  ```
					- Notice how in the above examples, the scope of each tag shrinks as we write. Make sure not to overly spam tags, this approach should help reducing spam while also boosting connections.
- # Namespaces
  collapsed:: true
	- In general, namespaces can and should typically be avoided due to them making linking less readable. In most cases, tags inside a page are often sufficient enough to model the relationships between ideas. However, there are a few use-cases when namespaces can serve to be useful.
	- ## When are name spaces okay?
		- So then, when should you use a namespace? Namespaces should only be used when you are writing for a topic and its tangentially related to specific theme/goal AND it is very unlikely that you will be linking to it from other notes. Additionally, you need these notes easily findable.
		- One way you can think of namespaces is like a filling cabinet for related ideas. In the example below, the `[[Film Review]]` namespace acts as a filing cabinet holding all the reviews:
			- **Examples:
				- ```
				  # Correct:
				  [[Film Review]]
				  [[Film Review/Inception]]
				  [[Film Review/Toy Story 3]]
				  
				  You are unlikely to ever link to this page from another page
				  AND your notes are tangentally related.
				  ```
				- ```
				  # Incorrect
				  [[Animals]]
				  [[Animals/Cats]]
				  [[Animals/Dogs/Poodle]]
				  
				  This namespaces theme is not specific enough. Additionally, using it
				  makes using links hard to read.
				  ```
			- ## Naming Conflicts
			- Namespaces are also acceptable if you are trying to avoid naming conflicts; however, there are better ways to handle name conflicts. Take for instance, how wikipedia resolves name conflicts. See below:
				- ```
				  If you have a page for the linux command "cat"
				  and a page for the animal cat, both can't use the same page name.
				  Thus using a namespace is a way to differentiate the two.
				  [[cat]]
				  [[command/cat]]
				  
				  However, the Wikipedia style naming is the better choice, see below:
				  [[cat]]
				  [[Cat (Linux Command)]]
				  ```
				- Why is the wikipedia style better? When you are writing and creating a new link, the suggested names will correctly appear as you type, unlike with namespaces.
				- ### The preferred way  to resolve name conflicts
				- We can take this approach and make it better with the use of nested loops, see below:
					- ```
					  [[Cat]]
					  [[Cat [[Linux]]]]
					  ```
						- ![image.png](../assets/image_1698715103386_0.png)
				- All though this method is arguably uglier then the wikipedia approach, it has one major benefit, It can help make you notes more uniformed due to it  again suggesting  page names. For instance, if you were to write in parentheses like with the wikipedia approach, there is no suggested names to use when creating new pages, this can lead to sloppy page naming such as follows:
					- ```
					  [[Cat (Linux Command)]]
					  
					  [[touch (Command)]]
					  
					  [[ls (Unix Command)]]
					  
					  One could easily see how different naming schemes could accidentally
					  be created.
					  ```
	- ## Special Namespaces:
	  collapsed:: true
		- ###  Functional Namespaces:
			- **[[Graph]]**
				- This namespace refers to this graph itself. Its functional purpose is aid in the upkeep and maintenance of the graph by establishing standards and creating utility tags.
					- `[[Graph/ISSUE]]` should be written when you notice a page is not adhering to the style guide. By flagging it, you can quickly find it in the reference section and fix later.
					- ` [[Graph/Style Guide]] ` (this page) contains the style guide used across this Logseq graph.
			- **[[Logseq]]**
				- If you are in need of Logseq documentation or tutorials, this namespace houses all related pages.
			- **[[Archive]]**
				- The purpose of this namespace is to archive unneeded pages and namespaces. Instead of deleting pages, make them a child of this name space, and disable
		- ### Data Type Namespace:
		  collapsed:: true
			- Data Type namespaces is the name applied to certain namespaces on this graph. Typically, they share the following properties:
				- Each page apart of this namespace use identical formatting and page props.
				  logseq.order-list-type:: number
				- The root node of the name space is disabled in the graph view, as displaying this provides no meaningful information. For example, don't want the root node for Document to display, because having our graph connecting every document together tells us nothing. 
				  logseq.order-list-type:: number
				  
				  By doing so, we can leverage the power of namespaces for organizing, while also not having  it affect the graph view.  i.e, we can quickly see a list of all documents we have by viewing the hierarchy section in the root node. 
				  
				  This allows us to automatically import in notes from services like Readwise and to quickly find them, with out having to search for names.
			- **[[Document]]**
				- {{embed ((65402583-680b-4999-9244-b8550f5ed47b))}}
				- **Formating:**
					- title::
					  full-title::
					  abbreviated-title::
					  cover:: ![Image]()
					  start::
					  end::
					  status::
					  document-type::
					  tags::
					  template:: namespace/document
					- Example:
						- ```
						  title:: The Document's Logseq page title
						  full-title:: Document's Full Title
						  abbreviated-title:: Shortened Version of the Document's Title.
						  cover:: ![Image](Link to cover image if applicable.)
						  start:: [[Link to Journal Date of Creation]]
						  end:: [[Link to Journal Date when Finished Reading]]
						  status:: (either Reading, Finished, or Unread)
						  document_type:: the type of doccument, eg. Book, Article, etc.
						  tags:: #[[Your tag here]]
						  ```
		-
		-
-