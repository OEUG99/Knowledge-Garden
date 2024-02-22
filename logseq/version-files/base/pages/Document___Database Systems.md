category:: [[Book]]
status:: Reading
cover:: ![Image](https://i.gr-assets.com/images/S/compressed.photo.goodreads.com/books/1172986053l/236665._SX318_.jpg){:height 172, :width 98}
title:: Document/Database Systems
abbreviated-title:: Database Systems
tags:: #[[Graph/ISSUE]]
- # 4: High-Level Database Models
  heading:: 1
	- ## 4.1 : The Entity/Relationship Model
	  heading:: 2
		- The entity relationship model consists of three principal element types:
			- 1. Entity sets
			  2. Attributes
			  3. Relationships
		- ### 4.1.1 Entity Sets
		  heading:: 3
			- An **entity** is an abstract object of some sort, and a collection of similar entities forms an **entity set**
				- entity sets bare a resemblance to a class of objects.
					- however, you won't see methods on this, i.e. entity sets are only concerned with the structure of data and not the operations on said data.
			- ## 4.12 Attributes
			  heading:: 2
				- Entity sets have associated **attributes** which are properties of the entities in that set.
			- ### 4.13 Relationships
			  heading:: 3
				- **Relationships** are connections among two or more entity sets.
			- ## 4.14 Entity-Relationship Diagrams
			  heading:: 2
				- Entity sets are represented by rectangles
				- Attributes are represented by ovals
				- Relationships are represented by diamonds.
			- ## 4.16 Multiplicity of Binary E/R Relationships:
			  heading:: 2
				- In a binary entity-relationship diagram, a relationship is a connection between two entities, indicating that there is an association or interaction between them.
				- The multiplicity of a binary E/R relationship specifies the number of instances of one entity that can be associated with the other entity through the relationship.
				- There are three types of multiplicities in a binary relationship:
					- 1. One to One (1:1) - a relationship where one instance of an entity is associated with one instance of another entity. In an ER diagram,  1:1 is represented by an arrow pointing both ways.
					  2. One to Many (1:N): In this type of relationship an entity can be associated with many instances of another entity, but each instance of the other entity can be associated with only one instance of the first entity. (Example: one department can have many employees, but each employee can belong to only one department.)  In an ER diagram, 1:N is represented as as one arrow going to the side that has 1 bound.
					  3. Many to Many (M:N): in this type of relationship, many instances of an entity can be associated with many instances of another entity. (example: a student can enroll in many courses, and each course can have many students enrolled in it). In an E.R. Diagram, no arrow is used.
					- General rule for arrows: arrows indicate multiplicity, an arrow means "at most one".
			- ## 4.17 Multiway relationships:
			  heading:: 2
				- In a multiway relationship, an arrow pointing to an entity set E means that if we select one entity from each of the other entity sets in that relationship, those relationship are related to at most one entity in E. ![CleanShot 2023-02-28 at 14.28.06@2x.png](../assets/CleanShot_2023-02-28_at_14.28.06@2x_1677612490464_0.png)
			- # 4.18 Roles in Relationships.
			  heading:: 1
				- it is possible that one entity set appears two or more tiems in a single relationship. If so, we draw as many lines from the relationship to the entity set as the entity set appears in the relationship.
				- Each line in the entity set represents a different *role* that the entity set plays in the relationship. We therfore label teh edges between the enetity set and relationships by names, which we call " roles."
				- Example:
					- For the relationship sequel-of between entity set Movies and itself. ![CleanShot 2023-02-28 at 14.30.57@2x.png](../assets/CleanShot_2023-02-28_at_14.30.57@2x_1677612671290_0.png)
					- ![CleanShot 2023-02-28 at 15.26.00@2x.png](../assets/CleanShot_2023-02-28_at_15.26.00@2x_1677615963884_0.png)
					- ![CleanShot 2023-02-28 at 16.06.41@2x.png](../assets/CleanShot_2023-02-28_at_16.06.41@2x_1677618416963_0.png)
					- ## 4.1.9 Attributes on relationships
					  heading:: 2
						- not neccessary, but sometimes cool. any attribute on a relationship can be represented as a new entity.
						- ![CleanShot 2023-02-28 at 15.55.31@2x.png](../assets/CleanShot_2023-02-28_at_15.55.31@2x_1677617738935_0.png){:height 464, :width 596}
					- ## 4.1.10 Converting multiway relationships to Binary
					  heading:: 2
						- It is useful to observe that any relationship connecting more than two entity sets can be converted to a collection of binary, many-to-one relationships.
					- ### 4.1.1 Subclasses in the E/R Model
					  heading:: 3
						- We connect an entity set to tis subclass using a relationship called *isa*. This is denoted as a triangle.
						- ![CleanShot 2023-02-28 at 16.07.21@2x.png](../assets/CleanShot_2023-02-28_at_16.07.21@2x_1677618446247_0.png)
						- ![CleanShot 2023-02-28 at 16.07.55@2x.png](../assets/CleanShot_2023-02-28_at_16.07.55@2x_1677618507560_0.png)
					- ### constraints in the e/r model
					  heading:: 3
						- every entity set must have a key, although in some cases -- isa-hierarchies and "weak" entity sets, the key actually belongs to another entity set.
						- There can be more the none possible key for an entity set. However, it is customary tp pick one as the "primary key", and to act as if that were the only key.
						- When an entity set is involved in an isa-heirarchy, we require that the root entity set have all attributes needed for a key, and that the key for each entity is found from its component in the root entity set, regardless of how many entity sets in the hierarchy have components for the entity.
					- keys in the er model are represented via underlines in attributes
- ## 3.1.1 Definition of Functional Dependency:
  heading:: 2
	- A functional dependency on a relation R is a statement of the form "if two tuples of R agree on all attributes A1,A1...An (i.e. the tuples have the same values in their respective components for each of these attributes), then they must also agree on all lists of attributes B1, b2....bm.
	- We write this formally as a1,a2...An -> b1,b2.. Bm
	- ![CleanShot 2023-03-01 at 16.53.26@2x.png](../assets/CleanShot_2023-03-01_at_16.53.26@2x_1677707616714_0.png)
	- If we are sure that every instance of a relation R will be one in which a given FD is true, then we say that R satisfies FD.
	- It is important to remember that when we say that R satisifies an FD f, we are asserting a contraint on R, not just saying something about one particualr instance of R.
	- ![CleanShot 2023-03-01 at 17.20.29@2x.png](../assets/CleanShot_2023-03-01_at_17.20.29@2x_1677709234413_0.png)
- ## 3.13 Superkeys
  heading:: 2
	- a set of attributes that contians a key is called a *superkey*, short for "superset of a key.", thus every key is a superkey. However, some superkeys are not (minimal) keys. Note that every suuperkey satisifies the first condition of a key: it functionally determines all other attributes of the relation. However, a superkey need not satisfy the second condition: minimality
	- ![CleanShot 2023-03-01 at 17.31.19@2x.png](../assets/CleanShot_2023-03-01_at_17.31.19@2x_1677709884586_0.png)
- ## 3.2 Rules about functional dependencies
  heading:: 2
	-
- ## 5: Algebraic and Logical Query Languages:
  heading:: 2
	- ## 5.1 Relational Operations on Bags
	  heading:: 2
		- Why do we use bags?
			- Take the union of two relations as bags, we simply copy one relation and add to the copy all tuples of the other relation. There is no need to eliminate duplicate copies of a tuple that happens to be in both relations.
			- When we project relation as sets, we need to compare each projected tuple with all the other projected tuples, to make sure that each projection appears only once. However, if we can accept a bag as the result ,then we simply project each tuple and add it to the result; no comparison with other project tuples is necessary.
			-