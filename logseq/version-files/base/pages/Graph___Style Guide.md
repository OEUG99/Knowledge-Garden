# Namespaces
	- Namespaces should only be used when you are writing for a topic and its tangentially related to specific theme/goal AND it is very unlikely that you will be linking to it from other notes. Additionally, you need these notes easily findable.
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
	- ## Special Namespaces:
		- Special Namespaces:
		- ###  Functional Namespaces:
			- **[[Graph]]**
				- This namespace refers to this graph itself. Its functional purpose is aid in the upkeep and maintenance of the graph by establishing standards and creating utility tags.
					- `[[Graph/ISSUE]]` should be written when you notice a page is not adhering to the style guide. By flagging it, you can quickly find it in the reference section and fix later.
			- **[[Logseq]]**
				- If you are in need of Logseq documentation or tutorials, this namespace houses all related pages.
			- **[[Archive]]**
				- The purpose of this namespace is to archive unneeded pages and namespaces. Instead of deleting pages, make them a child of this name space, and disable
		- ### Data Type Namespace:
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