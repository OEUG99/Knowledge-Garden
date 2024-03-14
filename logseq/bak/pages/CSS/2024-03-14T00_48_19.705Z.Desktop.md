title:: CSS
category:: [[Front-End Development]]
tags:: [[Programing]] [[Website Development]], [[Front-End Development]]

- # Introduction to CSS
  heading:: 1
	- CSS follows the following format:
	  ```css
	  selector 
	  {
	  property: value;
	  }
	  ```
	- css consists of declarations (the individual things inside the brackets, and declaration blocks (the collection of things inside the brackets))
	- There are two ways to attach the Style Sheet to a doccument:
		- **Embedded Style Sheets**
			- By using the `<style>` element in html, you can insert your style sheet.
			- Example:
			  ```html
			  <head>
			  <title> Title goes here </title>
			  <style>
			    /* style sheet goes here */
			  </style>
			  </head>
			  ```
		- **Inline Style Sheet**
			- You can apply property values to a single element via the html `style` attribute
			- Example:
			  ```html
			  <h1 style="color: red"> Introduction</h1>
			  ```
	- ## CSS Inheritance
	  heading:: 2
		- ![html_hierarchy.webp](../assets/html_hierarchy_1666461978258_0.webp)
		- "An element that is directly contained within another element (with no intervening hierarchical levels) is said to be the *child* of that element. Conversely the containing element is the *parent*. For example, the `em` element is the child of the `p` element, and the `p` element is its parent" (Page 247)
		- Thus, if we write a style rule for `p`, these rules will also be applied to `img` since `p` is the parent of `img`.
	- ## Cascading in CSS
	  heading:: 2
		- "Css allows you to apply several style sheets to the same document, which means there are bound to be conflict." (page 249)
		- The *cascade* refers to when many sources of style information fight for control of the elements
		- ## Priority operates as follows:
		  heading:: 2
			- 1. author style sheet (the author of the site's provided style sheet)
			  2. user style sheet (a style sheet a user applies themself)
			  3. user agent style sheet (the default for a web browser)
			- When two rules in a style sheet conflict, the type of selector is used to determine the winer.
				- The more specific the selector, the more weight is given.
				- Example:
				  The selector that includes ID name (`#intro`) is more specific then a general element selector (like `p`)
			- ## Rule Order
			  heading:: 2
				- After all the style sheets have been sorted by priority, there are likely to be conflict with rules of equal length. eg:
				  ```html
				  <style>
				  p {color: red; }
				  p {color: blue; }
				  p {color: yellow; }
				  </style>
				  ```
				- The last rule will have the final say, everything prior in some sense is being overwritten.
		- ## The Box Model
		  heading:: 2
			- The browser sees every element on the page (both block and inline) as being contained in a little rectangular box.
			- Basically, everything is a box inside a box, etc. If you were to add the property `border:` to every element, you would see these boxes.
		- ## Group Selectors
		  heading:: 2
			- The group selector allows you to provide the same properties to a group of elements. It uses the following format:
			  ```css
			  h1, h2, p, em, img { border: 1px solid blue;}
			  ```
		-