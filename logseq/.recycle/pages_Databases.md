- [[Software Engineering]]
- # Relational Algebra
  heading:: 1
	- ### Intersections:
	  heading:: 3
		- All the tuples both in R1 an in R2, denoted as: R1 N R2.
		- R1 N R2 has the same schema as R1,R2.
		- Example:
			- UnionizedEmployes N retired employees
		- Intersection is derived: r1 N r2 = r1 - (r1 - r2)
		- Proof: {insert here later}
	- ### Theta join:
	  heading:: 3
		- A join that involves a predicate (theta symbol here), denited as R1 (theta join symbol) R2
		- Input schemas: R1(A1,A2, ..., An), R2(B1, B2, ..., BM)
		- Theta