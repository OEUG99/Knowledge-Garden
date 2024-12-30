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
			- Where possible, `const`