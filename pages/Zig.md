tags:: [[Programming Language]]

- ![image.png](../assets/image_1735701059603_0.png){:height 268, :width 534}
- Preface: much of these notes are taken from: https://zig.guide/
- ## Syntax
	- ### Assignment
	  collapsed:: true
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
	  collapsed:: true
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
	  collapsed:: true
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
	  collapsed:: true
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
	  collapsed:: true
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
			- ### Custom Step Size
				- ```zig
				  const std = @import("std");
				  
				  pub fn main() void {
				      for (0..10:2) |i| {
				          std.debug.print("{}\n", .{i});
				      }
				  }
				  ```
			- ### Iterating With Index
				- ```zig
				  const std = @import("std");
				  
				  pub fn main() void {
				      const arr = [_]i32{1, 2, 3, 4};
				      for (arr) |val, idx| {
				          std.debug.print("index: {}, value: {}\n", .{idx, val});
				      }
				  }
				  ```
	- ## Functions
	  collapsed:: true
		- All function arguments are immutable. if a copy is needed the user must explicityly make one.
			- example:
			  ```zig
			  fn calculateNewPrice(price: u32, discount: u32) u32 {
			      let mut discounted_price = price; // Make a local mutable copy
			      discounted_price -= discount;    // Modify the local copy
			      return discounted_price;         // Return the new value
			  }
			  
			  fn main() {
			      let original_price = 100; // Immutable by default
			      let discount_amount = 20;
			  
			      let new_price = calculateNewPrice(original_price, discount_amount);
			  
			      println!("Original Price: {}", original_price); // Outputs: 100
			      println!("Discounted Price: {}", new_price);    // Outputs: 80
			  }
			  ```
		- It is also possible to use recursion, though when recursion is used the compiler is no longer able to determine the maximum stack size, which may result in unstable behavior and potential buffer overflows.
			- ```zig
			  fn fibonacci(n: u16) u16 {
			      if (n == 0 or n == 1) return n;
			      return fibonacci(n - 1) + fibonacci(n - 2);
			  }
			  
			  test "function recursion" {
			      const x = fibonacci(10);
			      try expect(x == 55);
			  }
			  ```
		- Variables are snake_case, functions are camelCase
		- only in a function can values be ignored using `_`.
			- Example:
			  ```zig
			  _ = 10;
			  ```
	- ## Defer
	  collapsed:: true
		- Defer is used to execute a statement upon exiting the current block.
			- example:
			  ```zig
			  defer x += 2;
			  ```
		- When multiple defers are used in the same code block, upon statement execution, the defers are then executed in **reverse order.**
			- This reflects/mimics the behavior of the stack for resource management, and uses a LIFO (Last in, First Out) paradigm.
			- Example:
			  ```zig
			          defer x += 2;  // Deferred action 1
			          defer x /= 2;  // Deferred action 2
			  
			  // action 2 will run before action 1
			  ```
		- Defers are useful for clearing up resources when they are no longer needed. Instead of remembering to manually free them up, you can defer the clean up statement right next to the statement that allocates the resources.
	- ## Errors
		- Errors in zig act sorta like enums, where each error in the set is a value. Zig has no exceptions.
			- ```zig
			  const FileOpenError = error{
			      AccessDenied,
			      OutOfMemory,
			      FileNotFound,
			  };
			  ```
			- if one error set is a ubset of another, zig allows for error sets to be coerced into their supersets.
				- example:
				  ```zig
				  const FileOpenError = error{OutOfMemory, PermissionDenied, NotFound};
				  ```
					-
					- Here, `FileOpenError` is a **superset** of `AllocationError`, because `OutOfMemory` is part of both error sets.
			- An error set type and another type can be combined with the `!` operator to form an error union type. Values of these types may be an error value or a value of the other type.
			- Example:
			  ```zig
			  test "error union" {
			      const maybe_error: AllocationError!u16 = 10;
			      const no_error = maybe_error catch 0;
			  
			      try expect(@TypeOf(no_error) == u16);
			      try expect(no_error == 10);
			  }
			  ```
			- functions often return error unions, we can catch errors and handle them doing what is called **payload capturing**
				- example:
				  ```zig
				  fn failingFunction() error{Oops}!void {
				      return error.Oops;
				  }
				  
				  failingFunction() catch |err| {
				          try expect(err == error.Oops);
				          return;
				      };
				  ```
			- the `try x` syntax is a shortcut for the `x catch |error| return err`.
			- Zig's `try` and `catch` operate completely different then try-catch in other languages.
			- [`errdefer`](https://ziglang.org/documentation/master/#errdefer) works like [`defer`](https://ziglang.org/documentation/master/#defer), but only executing when the function is returned from with an error inside of the [`errdefer`](https://ziglang.org/documentation/master/#errdefer)'s block.
			- example:
			  ```zig
			  const expect = @import("std").testing.expect;
			  
			  fn failingFunction() error{Oops}!void {
			      return error.Oops;
			  }
			  
			  var problems: u32 = 98;
			  
			  fn failFnCounter() error{Oops}!void {
			      errdefer problems += 1;
			      try failingFunction();
			  }
			  
			  test "errdefer" {
			      failFnCounter() catch |err| {
			          try expect(err == error.Oops);
			          try expect(problems == 99);
			          return;
			      };
			  }
			  ```
			- Error unions returned from a function can have their error sets inferred by not having an explicit error set. This inferred error set contains all possible errors that the function may return.
				- example:
				  ```zig
				  fn createFile() !void {
				      return error.AccessDenied;
				  }
				  
				  test "inferred error set" {
				      //type coercion successfully takes place
				      const x: error{AccessDenied}!void = createFile();
				  
				      //Zig does not let us ignore error unions via _ = x;
				      //we must unwrap it with "try", "catch", or "if" by any means
				      _ = x catch {};
				  }
				  ```
				- `anyerror` is the global error set, which due to being the superset of all error sets, can have an error from any set coerced to it. Its usage should be generally avoided.
	- ## Switch Statements
		- In zig, `switch` works both as a statement and an expression.
		- **Every** possible value of the type being switched on must be accounted for, either with a specific case, or an `else` branch. This ensures no undefined behavior due to missing cases.
		- Zig cases don't "fall through", like with out Switch cases work on C++.
			- Example of a switch statement:
			  ```zig
			  const std = @import("std");
			  
			  pub fn main() void {
			      const number = 2;
			  
			      const result = switch (number) {
			          1 => "One",
			          2 => "Two",
			          3 => "Three",
			          else => "Other",
			      };
			  
			      std.debug.print("{}\n", .{result});
			  } 
			  ```
			- Example of a switch expression:
			  ```zig
			   var x: i8 = 10;
			      x = switch (x) {
			          -1...1 => -x,
			          10, 100 => @divExact(x, 10),
			          else => x,
			      };
			  ```
	- ## Runtime Safety
		- It is recommended for developers to use the runtime safety features that zig has to offer. Zig is able to see detectable illegal behavior and cause a panic when safety is on.
		- Runtime safety protects you against things such out of bounds indices.
		- If you so wish though, you can disable runtime safety by using the built-in function as such in your code:
		  ```zig
		  @setRuntimeSafety(false);
		  ```
			- Note: the `@` is used to denote a built-in function.
		- ### Unreachable
			- `unreachable` are a type of assesertion to the compiler, that tell the compiler a certain branch is impossible. If we somehow reach an unreachable, this can be caught by runtime safety as it is treated as a detectable illegal behavior.
			- example:
			  ```zig
			  fn asciiToUpper(x: u8) u8 {
			      return switch (x) {
			          'a'...'z' => x + 'A' - 'a',
			          'A'...'Z' => x,
			          else => unreachable,
			      };
			  }
			  ```
	- ## Pointers
		- Normal pointers in Zig cannot have 0 or null as a value. They follow the syntax `*T`, where `T` is the child type.
		- Referencing is done with `&variable`, and dereferencing is done with `variable.*`.
		- ```zig
		  fn increment(num: *u8) void {
		      num.* += 1;
		  }
		  
		  test "pointers" {
		      var x: u8 = 1;
		      increment(&x);
		      try expect(x == 2);
		  }
		  ```
		- Trying to set a `*T` to the value 0 is detectable illegal behaviour.
		- 0 often represents a null pointer as there is no zero location in memory.
		- Zig also has const pointers, which cannot be used to modify the referenced data. Referencing a const variable will yield a const pointer.
		- ### Many-Item Pointers
			- Most programs need to keep track of buffers which don't have compile-time known lengths. Many-item pointers are used for these. These act similarly to their single-item counterparts, using the syntax `[*]T` instead of `*T`.
			- ![image.png](../assets/image_1735704290047_0.png)