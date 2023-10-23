- /template
  file-path:: ../assets/Eloquent_JavaScript_1666916482303_0.pdf
- ![Eloquent_JavaScript.pdf](../assets/Eloquent_JavaScript_1666916482303_0.pdf)
- # Chapter 1
  heading:: 1
	- JavaScript was introduced in 1995 as a way to add programs to web pages in the Netscape Navigator browser.
	  ls-type:: annotation
	  hl-page:: 24
	  hl-color:: yellow
	- a standard document was written to describe the way the JavaScript language should work so that the various pieces of software that claimed to support JavaScript were actually talking about the same language. This is called the ECMAScript standard, after the Ecma International organization that did the standardization.
	  ls-type:: annotation
	  hl-page:: 25
	  hl-color:: yellow
	- JavaScript is ridiculously liberal in what it allows
	  ls-type:: annotation
	  hl-page:: 26
	  hl-color:: yellow
	- Web browsers are not the only platforms on which JavaScript is used. Some databases, such as MongoDB and CouchDB, use JavaScript as their scripting and query language.
	  ls-type:: annotation
	  hl-page:: 27
	  hl-color:: yellow
	- JavaScript is also used in more traditional websites to provide various forms of interactivity and cleverness.
	- When you write something inside ${} in a template literal, its result will be computed, converted to a string, and included at that position. The example produces “half of 100 is 50”.
	  ls-type:: annotation
	  hl-page:: 39
	  hl-color:: yellow
	- Backtick-quoted strings, usually called template literals, can do a few more tricks. Apart from being able to span lines, they can also embed other values.\`half of 100 is ${100 / 2}\`
	  ls-type:: annotation
	  hl-page:: 39
	  hl-color:: yellow
	- You can use single quotes, double quotes, or backticks to mark strings, as long as the quotes at the start and the end of the string match.
	  ls-type:: annotation
	  hl-page:: 37
	  hl-color:: yellow
	- typeof operator, which produces a string value naming the type of the value you give it.
	  ls-type:: annotation
	  hl-page:: 39
	  hl-color:: yellow
	- JavaScript supports three logical operators: and, or, and not. These can be used to “reason” about Booleans.
	  ls-type:: annotation
	  hl-page:: 42
	  hl-color:: yellow
		- The && operator represents logical and. It is a binary operator, and its result is true only if both the values given to it are true.
		  ls-type:: annotation
		  hl-page:: 42
		  hl-color:: yellow
		- The || operator denotes logical or. It produces true if either of the values given to it is true.
		  ls-type:: annotation
		  hl-page:: 42
		  hl-color:: yellow
		- Not is written as an exclamation mark (!). It is a unary operator that flips the value given to it—!true produces false, and !false gives true.
	- The last logical operator I will discuss is not unary, not binary, but ternary, operating on three values
	  ls-type:: annotation
	  hl-page:: 43
	  hl-color:: yellow
		- ```JavaScript
		  console.log(true ? 1: 2);
		  // -> 1
		  console.log(false ? 1: 2);
		  // -> 2
		  ```
		- The value on the left of the question mark “picks” which of the other two values will come out. When it is true, it chooses the middle value, and when it is false, it chooses the value on the right.
		  ls-type:: annotation
		  hl-page:: 44
		  hl-color:: yellow
	- There are two special values, written null and undefined, that are used to denote the absence of a meaningful value.
	  ls-type:: annotation
	  hl-page:: 44
	  hl-color:: yellow
	- Many operations in the language that don’t produce a meaningful value (you’ll see some later) yield undefined simply because they have to yield some value.
	  ls-type:: annotation
	  hl-page:: 44
	  hl-color:: yellow
	- The difference in meaning between undefined and null is an accident of JavaScript’s design, and it doesn’t matter most of the time.
	  ls-type:: annotation
	  hl-page:: 44
	  hl-color:: yellow
	- When an operator is applied to the “wrong” type of value, JavaScript will quietly convert that value to the type it needs, using a set of rules that often aren’t what you want or expect. This is called type coercion.
	  ls-type:: annotation
	  hl-page:: 45
	  hl-color:: yellow
	- The null in the first expression becomes 0, and the "5" in the second expression becomes 5 (from string to number). Yet in the third expression, + tries string concatenation before numeric addition, so the 1 is converted to "1" (from number to string).
	  ls-type:: annotation
	  hl-page:: 45
	  hl-color:: yellow
	- When something that doesn’t map to a number in an obvious way(such as "five" or undefined) is converted to a number, you get the value NaN.
	  ls-type:: annotation
	  hl-page:: 45
	  hl-color:: yellow
		- Further arithmetic operations on NaN keep producing NaN, so if you find yourself getting one of those in an unexpected place, look for accidental type conversions.
		  ls-type:: annotation
		  hl-page:: 45
		  hl-color:: yellow
	- When comparing values of the same type using ==, the outcome is easy to predict: you should get true when both values are the same, except in the case of NaN. But when the types differ, JavaScript uses a complicated and confusing set of rules to determine what to do
	  ls-type:: annotation
	  hl-page:: 45
	  hl-color:: yellow
	- In most cases, it just tries to convert one of the values to the other value’s type. However, when null or undefined occurs on either side of the operator, it produces true only if both sides are one of null or undefined.
	  ls-type:: annotation
	  hl-page:: 45
	  hl-color:: yellow
	- When you do not want any type conversions to happen, there are two additional operators: \=\=\= and \!\=\=. The first tests whether a value is precisely equal to the other, and the second tests whether it is not precisely equal. So "" === false is false as expected.
	  ls-type:: annotation
	  hl-page:: 46
	  hl-color:: blue
	- The logical operators && and || handle values of different types in a peculiar way. They will convert the value on their left side to Boolean type in order to decide what to do, but depending on the operator and the result of that conversion, they will return either the original left-hand value or the right-hand value.
	  ls-type:: annotation
	  hl-page:: 46
	  hl-color:: yellow
	- The || operator, for example, will return the value to its left when that can be converted to true and will return the value on its right otherwise.
	  ls-type:: annotation
	  hl-page:: 47
	  hl-color:: yellow
	- This has the expected effect when the values are Boolean and does something analogous for values of other types.
	  ls-type:: annotation
	  hl-page:: 47
	  hl-color:: yellow
	- We can use this functionality as a way to fall back on a default value. If you have a value that might be empty, you can put || after it with a replacement value. If the initial value can be converted to false, you’ll get the replacement instead. The rules for converting strings and numbers to Boolean values state that 0, NaN, and the empty string ("") count as false, while all the other values count as true. So 0 || -1 produces -1, and "" || "!?" yields "!?".
	- The && operator works similarly but the other way around.
	  ls-type:: annotation
	  hl-page:: 47
	  hl-color:: yellow
	- Another important property of these two operators is that the part to their right is evaluated only when necessary.
	  ls-type:: annotation
	  hl-page:: 47
	  hl-color:: yellow
	- This is called short-circuit evaluation.
	  ls-type:: annotation
	  hl-page:: 47
	  hl-color:: yellow
- # Chapter 2
  heading:: 1
- To catch and hold values, JavaScript provides a thing called a binding, or variable:
  ls-type:: annotation
  hl-page:: 51
  hl-color:: yellow
  ```let caught = 5 * 5```
  - The special word (keyword) let indicates that this sentence is going to define a binding. It is followed by the name of the binding and, if we want to immediately give it a value, by an = operator and an expression.
  ls-type:: annotation
  hl-page:: 51
  hl-color:: yellow
  id:: 635c3f1f-b740-4cba-8927-24a200c8f328
  - The = operator can be used at any time on existing bindings to disconnect them from their current value and have them point to a new one.
  ls-type:: annotation
  hl-page:: 51
  hl-color:: yellow
  id:: 635c3f68-815c-4fa7-a43b-f5701340ba04
  - A program can access only the values that it still has a reference to
  ls-type:: annotation
  hl-page:: 51
  hl-color:: yellow
  id:: 635c3f9d-b049-4734-8b82-756c6886ac0f
  - The words var and const can also be used to create bindings, in a way similar to let.
  ls-type:: annotation
  hl-page:: 51
  hl-color:: yellow
  id:: 635c3fec-3e84-4347-b169-d38eeed9a981
  - ```JavaScript
  var name = "Ayda"; 
  const greeting = "Hello "; 
  console.log(greeting + name);
  // → Hello Ayda
  ```
- The first, var (short for “variable”), is the way bindings were declared in pre-2015 JavaScript
  ls-type:: annotation
  hl-page:: 53
  hl-color:: yellow
- The word const stands for constant. It defines a constant binding, which points at the same value for as long as it lives.
  ls-type:: annotation
  hl-page:: 53
  hl-color:: yellow
- Binding names can be any word. Digits can be part of binding names
  ls-type:: annotation
  hl-page:: 54
  hl-color:: yellow
- A binding name may include dollar signs 
  ls-type:: annotation
  hl-page:: 54
  hl-color:: yellow
- Words with a special meaning, such as let, are keywords, and they may not be used as binding names.
  ls-type:: annotation
  hl-page:: 54
  hl-color:: yellow
- The collection of bindings and their values that exist at a given time is called the environment. 
  ls-type:: annotation
  hl-page:: 55
  hl-color:: yellow
- When a program starts up, this environment is not empty. It always contains bindings that are part of the language standard, and most of the time, it also has bindings that provide ways to interact with the surrounding system.
  ls-type:: annotation
  hl-page:: 55
  hl-color:: yellow
- A function is a piece of program wrapped in a value. Such values can be applied in order to run the wrapped program
  ls-type:: annotation
  hl-page:: 55
  hl-color:: yellow
- Executing a function is called invoking, calling, or applying it.
  ls-type:: annotation
  hl-page:: 56
  hl-color:: yellow
- You can call a function by putting parentheses after an expression that produces a function value.
  ls-type:: annotation
  hl-page:: 56
  hl-color:: yellow
- alues given to functions are called arguments. 
  ls-type:: annotation
  hl-page:: 56
  hl-color:: yellow
- Most JavaScript systems (including all modern web browsers and Node.js) provide a console.log function that writes out its arguments to some text output device
  ls-type:: annotation
  hl-page:: 56
  hl-color:: yellow
- In browsers, the output lands in the JavaScript console
  ls-type:: annotation
  hl-page:: 56
  hl-color:: yellow
- Conditional execution is created with the if 
  ls-type:: annotation
  hl-page:: 59
  hl-color:: yellow
- The statement after the if is wrapped in braces ({ and }) in this example. The braces can be used to group any number of statements into a single statement, called a block.
  ls-type:: annotation
  hl-page:: 59
  hl-color:: yellow
- Looping control flow allows us to go back to some point in the program where we were before and repeat it with our current program state.
  ls-type:: annotation
  hl-page:: 62
  hl-color:: yellow
- A do loop is a control structure similar to a while loop. It differs only on one point: a do loop always executes its body at least once, and it starts testing whether it should stop only after that first execution.
  ls-type:: annotation
  hl-page:: 64
  hl-color:: yellow
- There is a special statement called break that has the effect of immediately jumping out of the enclosing loop.
  ls-type:: annotation
  hl-page:: 67
  hl-color:: yellow
- The continue keyword is similar to break, in that it influences the progress of a loop
  ls-type:: annotation
  hl-page:: 67
  hl-color:: yellow
- JavaScript has two ways of writing comments. To write a single-line comment, you can use two slash characters (//) and then the comment text after it.
  ls-type:: annotation
  hl-page:: 71
  hl-color:: yellow
- A section of text between /* and */ will be ignored in its entirety, regardless of whether it contains line breaks.
  ls-type:: annotation
  hl-page:: 72
  hl-color:: yellow