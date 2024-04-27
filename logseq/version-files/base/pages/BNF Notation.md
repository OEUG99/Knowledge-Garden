- BNF stands for **Backus Naur Form** notation. It is a formal method for describing the syntax of programming language
- ```
  name ::= expansion
  ```
	- The symbol ::= means “may expand into” and “may get replaced with.”
	- An expansion is an expression containing terminal symbols and non-terminal symbols, joined together by sequencing and selection.
	- A terminal symbol may be a literal like (“+” or “function”) or a category of literals (like integer).
	- ```
	  <term> ::= <factor> "*" <term>
	          |  <factor>
	  
	  <factor> ::= "(" <expr> ")"
	            |  <const>
	  
	  <const> ::= integer
	  ```
		- A vertical bar | indicates choice.
- ## Rules
	-