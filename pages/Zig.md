## Syntax
	- ### Assignment
		- You can assign with `const` or `var`, and type is defined after the variable name, as such:
			- ```zig
			  const x: i32 = 5;
			  var y: i32 = 2;
			  ```
			- `const`  and `var` must always have a value. If no value can be given, the `undefined` value can be used, it coerces to any type. See example:
				- ```zig
				  const a: i32 = undefined;
				  var b: u32 = undefined;
				  ```
			- Where possible, `const` values are preffered over `var`
	- ## Arrays
		- Arrays are denoted as `[N]T` where `N` is the number of elements, and `T` is the type of those elements.
		- We can use `_` when we define an array with elements inside of it IF we want to define the size of the array based on the initial number of elements.
			- ```zig
			  const a = [5]u8{ 'H', 'I'};
			  const b = [_]u8{'B', 'Y', 'E'};
			  ```
		- To get the size of any array, we can use the `len` field.
			-