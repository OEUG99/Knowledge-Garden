tags:: [[Programming Language]] [[Programming]]

	- # Binding operator:
	  heading:: 1
		- Check if `<pattern>` match for `<string>`
			- `<string>` =~ `/<pattern>/`
		- Check if there is not a `<pattern>` match for `<string>`
			- `<string>` !~ `/<pattern>/`
		-
- # Regex in perl
  heading:: 1
	- https://cloud.geno.gg/Qt9mbP
	- https://cloud.geno.gg/kNbCqU
	- https://cloud.geno.gg/EvlTEX
	- perl anchors:
		- ^ beginging of line
		- $ end of the line
		- \b matches at the start of word
		- \ba\b matches if a is in a complete word
		- https://cloud.geno.gg/Kf7eCV
	- back references examples:
	  ```perl
	  my $numbers = "5 6 7\n";
	  $numbers =~ /(d\) (d\) (d\)/\3 \2 \1;
	  print $numbers; #out puts 7 6 5
	  
	  # example of memory variables:
	  print my $sum = $1 + $2 +3 # prints the sum of our matches.
	  ```
- # print f formatting
  heading:: 1
	- https://www.tutorialspoint.com/perl/perl_printf.htm
	- https://cloud.geno.gg/86qEld
	- %s string
	- %d truncated decimal
	- %f float
- # I/O - Getting User Input
  heading:: 1
	- How do we get user input?
	- `my $user_input = <STDIN>;`
		- Note: this waits for the user to type hit return aka type a new line (\n)
		- We can use chomp() to remove it!
		- `chomp($user_input`) <-- removes new line from user input.
		- We can even combien the two in one line:
			- `chomp(my $user_input = <STDIN>);`
		- chomp is a function - it returns the number of times a new line was removed!
			- `my $num_nl_removed = chomp <STDIN>` <-- stores 1 in to num_nl_removed.
- # Interpolation of string
  heading:: 1
	- When a string is double quoted it is subject to variable interpolation.
	- `print "$name is my name!";`
	- how do you print a dolar sign then?
		- `print "$name is my name! I have \$10!"`
- # Hashes:
  heading:: 1
	- Each function: useful in while loops, can get you both key and value same time
	  ```perl
	  while ((my $name, my $price) = each %test) {
	  print "$name = $price \n";
	  }
	  ```
	- Exist function: chekcs if a key exists in a has
	  ```perl
	  my %fruit = ('orange' => 10, 'apple' => 100)
	  my %f = "orange"
	  
	  if (exists $fruit{$f}) {
	  print "The price of an orange is $fruit{$f}. \n"
	  }
	  ```
	- Delete function: removes a key-value pair from a hash table.
		- `NEEDS CODE HERE`
- # Control Structures:
  heading:: 1
	- if statements
		- if/elsif/else
	- Loop Structures -- While & until statments:
		- last operator - similar to the break operator in other languages like c++
		- next operator - jumps to the end of a the block, but does not jump outside it:
		  ```perl
		  while (expression) { 
		  stmt_1; 
		  stmt_2; 
		  next; 
		  stmt_3; 
		  # next jumps to here 
		  }
		  ```
	-
		- redo operator -  jumps to the start of a the block.
		  ```perl
		  while (expression) {
		  #  redo jumps to here
		   stmt_1;
		   stmt_2;
		   redo;
		   stmt_3;
		  }
		  ```
- # Arrays:
  heading:: 1
	- How do you make an array?
		- `my @array = ( 1, 56, 53, 643)`
	- You can get the last element of an array by doing the following:
		- `@array[-1]`
		- Negative indices allow for the looping backwards of an array.
	- How do you resize an array in perl?
		- `splice @array, 43` Note last argument determins where the new array will start.
	- How do you get elements 2 to 5 on an array?
		- `@array[2..5]`
	- What is the difference betweeen an array and a list?
		- Arrays are variables that store a list
		- a list is a collection of scalars.
	- How do you add a new item to the end of an array?
		- `push @array, 8` array will now have '8' as the last element. inserts new element.
	- How do you remove the last element from an array?
		- `pop @array`
		- you can store the value thats popped off like: `my $val = pop @array;`
	- How do you reverse an array?
		- `reverse(@array);`
	- How do you sort an array by ASCII?
		- `sort @array;`
	- How do you sort by a subroutine?
	  ```perl
	  sub by_even_odd 
	  {
	      my (@a, @b) = @_;
	      if (($a % 2 eq '0') and ($b % 2 ne '0')) { -1 }
	      elsif (($a % 2 ne '0') and ($b % 2 eq '0')) { 1 }
	      else { 0 }
	  }
	  ```
	  
	  ```perl
	  sub by_number 
	  {
	      my (@a, @b) = @_;
	      if ($a < $b ) { -1 }
	      elsif ($a > $b) { 1 }
	      else { 0 }
	  }
	  ```
	  
	  `sort by_number @array` <- 'by_number' is a subroutine.
	- How is Shift and unshift different from push and pop?
		- They are similar except shift & unshift work at the start of the array, where push and pop work at the end of the array
		- Shift gets whatever value that is shifted off, and also changes the value
		  ```perl
		  shift @array;
		  unshift @array, 1; 
		  ```
-