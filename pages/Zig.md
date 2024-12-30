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
			- ```zig
			  const array = [_]u8{ 'h', 'e', 'l', 'l', 'o' };
			  const length = array.len; // 5
			  ```
	- ## If-Expressions
		- If statements in zig work as you would expect, except they must resolve to `bool` meaning no implicity is possible.
			- ```zig
			  const expect = @import("std").testing.expect;
			  
			  test "if statement" {
			      const a = true;
			      var x: u16 = 0;
			      if (a) {
			          x += 1;
			      } else {
			          x += 2;
			      }
			      try expect(x == 1);
			  }
			  ```
		- If statements can also be used as expressions:
			- ```zig
			  test "if statement expression" {
			      const a = true;
			      var x: u16 = 0;
			      x += if (a) 1 else 2;
			      try expect(x == 1);
			  }
			  ```
	- ## While Loops
		- while loops in zig have three parts - a condition, a block, and a continue expression
			- with out a continue expression:
			  ```zig
			  test "while" {
			      var i: u8 = 2;
			      while (i < 100) {
			          i *= 2;
			      }
			      try expect(i == 128);
			  }
			  ```
			- with a continue expression:
			  ```zig
			  test "while with continue expression" {
			      var sum: u8 = 0;
			      var i: u8 = 1;
			      while (i <= 10) : (i += 1) {
			          sum += i;
			      }
			      try expect(sum == 55);
			  }
			  ```
			- with a break:
			  ```zig
			  test "while with break" {
			      var sum: u8 = 0;
			      var i: u8 = 0;
			      while (i <= 3) : (i += 1) {
			          if (i == 2) break;
			          sum += i;
			      }
			      try expect(sum == 1);
			  }
			  ```
	- ## For Loops
		- For loops are very similar to other languages in Zig.
			- ### Simple Range Loops
				- ```zig
				  const std = @import("std");
				  
				  pub fn main() void {
				      for (1..5) |i| {
				          std.debug.print("{}\n", .{i});
				      }
				  }
				  ```
			- ### Iterating Over an Array
				- ```zig
				  const std = @import("std");
				  
				  pub fn main() void {
				      var arr = [_]i32{10, 20, 30, 40};
				      for (arr) |val| {
				          std.debug.print("{}\n", .{val});
				      }
				  }
				  ```
			-