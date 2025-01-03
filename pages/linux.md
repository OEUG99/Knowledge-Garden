title:: Linux
tags:: [[Operating System]]

- # Lexical Analyzers & Lex Command
	- Lex is short for Lexical Analyzer.
	- A lexical analyzer reads in a stream of characters as input and produces a sewuqences of symvols called tokens as outputs.
		- They are useful for a variety of tasks.
	- The lex command is a tool to automatically create a lexical analyzer from a provided specification.
	- ### Lexical Analysis Terms
	  heading:: 3
		- A **token** is a group of characters having a collective meaning. (e.g id).
		- A **lexeme** is an actual character sequence forming a specific instance of a token (e.g. num).
		- a **pattern** is a rule describing how a particular token can be formed. This is usually done with regex. `(e.g. [A-Za-z_][A-Za-z_0-9]*))`
		- Characters between tokens are called **whitespace** (e.g. blanks, tabs, newlines, comments.)
	- #### Attributes for Tokens
	  heading:: 4
		- Tokens can have **attributes** that can be passed back to the function calling the lexical analyzer.
			- Constants
				- Value of the constant
			- Identifiers
				- pointer to a location where information is kept about the identifier.
	- #### General Approaches to Implementing Lexical Analyzers.
	  heading:: 4
		- Using a lexical-analyzer generator, such as the Lex command.
		- Write the lexican analyzer in a convention programming languages.
		- Write the lexican analyzer in assembly language.
	- #### Lex Command - A Lexical Analyzer Generator.
		- Can link with a lex library to get a main routine.
		- Can use as a function called yylex().
		- Easy to interface with yacc.
- # Make command
	- The make utility is used to:
		- Automate the execution of commands for file generation
		- Minimize the number of commands needed for rebuilding a target.
	- A makefiel describes:
		- A heirarchy of dependencies between individual files
		- command to generate each file.
	- There can be one or more target entries in a makefile. Each target entry in a make file has the following format:
	  ```makefile
	  target: dependency_file ...
	  command
	  ```
	- The target is a file. There can be one or more dependency files on which the target depends. There can be one or more commands each proceeded by a tab that comprise a rule for that target. Therese commands used to create or regenerate the target file.
	- A target is remade when the target file eitehr does not exist or has an older/date/time than one or more od the dependency files.
	- The targets and dependency files comrpise a DAG structure representing the dependencies between the different components.
	- The make utility recusrively checks each target against its dependencies, starting with the first target entry in the makefile.
	- Example Makefile:
	- ```makefile
	  expr.exe: expr.o lex.yy.o
	  gcc -g - o expr.exe expr.o lex.yy.o
	  expr.o: expr.c defs.h
	  gcc -g -c expr.c
	  lex.yy.o: lex.yy.c
	  gcc -g -c lex.yy.c
	  
	  lex.yy.c: scan.l
	  lex scan.l
	  ```
	-
	- <img src="https://mermaid.ink/img/ICBmbG93Y2hhcnQgQlQKCXN1YmdyYXBoIERpYWdyYW0gT2YgVGhlIEFib3ZlIE1ha2VmaWxlCgrCoMKgYVtleHByLmV4ZV0KCWJbZXhwci5vXQoJY1tsZXgueXkub10KCWRbZXhwci5jXQoJZVtkZWZzLmhdCglmW2xleC55eS5jXQoJZ1tzY2FuLmxdCglnLS0-ZgoJZi0tPmMKCWMtLT5hCglkLS0-YgoJZS0tPmIKCWItLT5hCiBlbmQK" />
	  collapsed:: true
	  {{renderer :mermaid_jcdpdkblafe}}
		- ```mermaid 
		  flowchart BT
		  subgraph Diagram Of The Above Makefile
		  
		  a[expr.exe]
		  b[expr.o]
		  c[lex.yy.o]
		  d[expr.c]
		  e[defs.h]
		  f[lex.yy.c]
		  g[scan.l]
		  g-->f
		  f-->c
		  c-->a
		  d-->b
		  e-->b
		  b-->a
		  end
		  ```
	- ### Ivoking Make Command
	  heading:: 3
		- General form:
			- `make [-f makefilename] [target]`
		- if no makefilename is given, then makelooks for a filecalled makefile or Makefile in that order. Make uses one of these files if found in the current directory.
		- By default make attempts to create the first target in the file. Alternatively, a user can specifcy a target within the makefile to make.
		  ```bash 
		  # Make the first target in makefile or Makefile. 
		  make 
		  
		  # Make the lex.yy.o target in makefile or Makefile. 
		  make lex.yy.o 
		  
		  # Make the first target in the makeexpr makefile. 
		  make -f makeexpr 
		  
		  # Make the expr.o target in the makeexpr makefile. 
		  make -f makeexpr expr.o 
		  ```
	- #### Defining symbols in a Makefile
	  heading:: 4
		- You can define a symbol in a makefile and refernce the symbol in multiple places.
		- General form of the definition.
			- symbol = definition.
		- General form of the reference.
			- $(symbol)
			  
			  ```Makefile
			  CC = gcc
			  CFLAGS = -g -c
			  
			  expr.exe: expr.o lex.yy.o
			  $(CC) -g - o expr.exe expr.o lex.yy.o
			  expr.o: expr.c defs.h
			  $(CC) $(CFLAGS) expr.c
			  lex.yy.o: lex.yy.c
			  $(CC) $(CFLAGS) lex.yy.c
			  
			  lex.yy.c: scan.l
			  lex scan.l
			  ```
	- #### Ctags: create tag file for Use with VI
	  heading:: 4
		- *ctags* is a unix utility that takes in a set of source files as input and creates a tags file as ouput.
		- the *tags* file contains for each function and macro:
			- object name.
			- File in which the object is defined.
			- pattern describing the location of the object.
		- General Form:
			- ctags *list_of_files*
		- Using the tag files
			- You can use the tags file with the vi (vim, gvim) editiors
			- Use the -t optio nwhen invoking vi. The editor will look in the current directory for the tags file and attempt to find the location of the function or macro in the appropriate file. If it finds it, then the file is opened and the sursor is positioned to the location.
			- `vi -t tag`
			- `vi -t main`
			- `vi -t max`
			- `ctags filename`
	- #### Source Level Debugging
	  heading:: 4
		- A source level debugger has a number of useful features that facilitates debugging problems assoicated with executign your program.
		- You have to create symbolic table information within the executable by using the -g option when compiling with gcc or G++.
		- This symbolic table informaiton includes the correspondance between:
			- Statements in the source code and locations of instructions in the executable.
			- Variables in the source code and locations int he data areas of executable.
	- #### GBD: Gnu DeBugger
	  heading:: 4
		- GBD is a line oriented debugger where actions are issued by typing i ncommands.
		- It can eb involved for executables vompiled by gcc or g++ with the option -g option.
		- General capabilities:
			- start/exiting your program from the debugger
			- Stopping and continuing the execution of your program
			- Examming the state of your program.
			- Changing state in your program.
		- Starting/exiting GBD:
			- bring up the gbd debugger by typing:
				- `gbd executable_name`
			- Initiate your executable by using the command:
				- `run [command-line arguments]`
					- command line arguments can include anythign that would normally appear after the exeutable name on the command line.
						- run-time options, filenames, I/o redirection, etc.
					- when no arguments are specified, then GBD uses teh arguments specifieid for the previous run command.
					- Exit the gbd debugger by typing:
						- `quit`
					- Can set a breakpoint to stop:
						- at a particula rsource line or function
						- when specificed condition occurs.
						- General form:
							- `break [linenun|function][if condition]
						- delete a break point by doing the following
							- `delete breakpoint_number`
						- until command executes your program
					- Listing source code at a specifined line or funciton:
						- `list [[filename:]linenum[,linenum]|[filename:]functionnane]`
	- #### DDD
	  heading:: 4
		- displays 4 different windows
			- Data window
			- source window
			- machine code window.
			- - GBD console where convential GBD comamnds can be typed.
			- DDD also has other plans which include commadns that can be selected wit ha mouse click.
	- #### Diff command
	  heading:: 4
		- the diff comamnd in unix compres two files and displays the difference between teh two files.
		- Useful in shell dscripts to detect differences between expected output and actual output.
	- #### Patch command:
	  heading:: 4
		- Takes the diff output and applies the commands to make the first file have the same contents as the second.
	- #### gvimdiff
	  heading:: 4
		- the utlity (g)vimdiff allows you to edit two or three files and visualize the differences.
		- ``gvimdiff file1 file2 [file3]```
	- #### cmp command:
	  heading:: 4
		- The cmp Unix utility just returns a status indicating if the files differ.
			- `0` if idential
			- `1` if differs
			- `>1` an error occured.
	- #### Gprof
	  heading:: 4
		- The gprof Unix utility produces an execution profile of the call graph of a program.
		- the profile is useful for finding out where most of the time is spent during the execution of your program.
		- A developer can use this information to tune the time-consuiming portions of a long running program.
		- how to use: `g++ -pg filename.cpp`
			- a gmon.out will be produced which can be used by running:
				- `gprof -b -A`
	- #### Spell checkers
	  heading:: 4
	- spell and ispell
		- `spell filenames`
		- `ispell filename ` <- interactive.
	- #### Printing:
	  heading:: 4
		- lpr
			- `lpr -#(num copies) -P(printername) -Z(option)` ques a print job for a given printer.
		- lpq
			- lpq used to display list of print jobs in the queue.
		- lprm
			- deletes a job from queue.
				- `lprm [-Pprinter] jobid`
		- pr
			- pr command is used to break up text files into pages for printing.
			- `pr [options] [files]`
				- -ln  set page length to n lines.
				- -wm set page width to m columns
				- +num begin printing a page num
				- -m merge files printing them side by side
				- -t omit the page heading and trailing blank lines.
		- a2ps
			- ascii formatter for printing.
			- unix utility formats text files for printing on a postscript printer. In other words, it converts text to postscript.
			- `a2ps text_files`
- # File mangement tools:
  heading:: 1
	- ## Gzip and Gunzip:
	  heading:: 2
		- gzip utility compresses a specified list of files. After compressing each specified file, it renames it to have a ".gz' extension
			- `gzip [filename]*`
		- the gunzip utility uncompresses a specified list of files that have been previously compressed with gzip.
			- `gunzip [filename]*`
	- ## Tar
	  heading:: 2
		- tar is a utility for creating and extracting archives. It was originally setup for archives on tape, but it now is mostly used for archives on disk. It is very useful for sending a set of files to someone over hte network. Tar is also useful for making backups.
			- `tar options filenames`
				- c - inserts file into a tar file
				- f - uses the name of the tar file that is specified
				- v - output the name of each file as it is inserted into or extracted from a tar file
				- x - extract the files from a tar file.
			- typical usage: `tar cvf tarfilename filenames`
	- ## Find
	  heading:: 2
		- The find unix utility recusrivelyt searches within a directory for files that match specified attributes.
			- `find [directory]+ operators`
	- ## DF and DU
	  heading:: 2
		- The df command displays the amount of disk used and available on all mounted file systems.
			- If you specify a filename, then it shows disk space that is available on the file system containing the file.
		- The du command writes the size of each directory and subdirectory in 1024 byte units. By default it uses the current directory. However, you can specify the set of files and directories for it to inspect. The -s option indicates to just print the total sum and not information for each file.
			- `du [-s] [filenames]`
	- ## Od
	  heading:: 2
		- The od command copies each input file to standard output and transforms the input data according to the output types specified in the options given in the command.
		- `od [options] [filename]`
	- ## nm:
	  heading:: 2
		- The nm utility prints the global names of functions and variables within object files or executables.
		- `nm [options] files`
		- ## Strip:
		  heading:: 2
		  the strip unix utility removes optiona symbol tables, debugging, and line number informatio nfrom an object file or executable. Strep is used to reduce the file storage required for these files.
		- `strip files`
	- ## sftp utility
	  heading:: 2
		- `sftp [hostname | user@hostname]`
- ### Process controll
  heading:: 3
	- ### Differeiences between process vs Executables
	  heading:: 3
		- A process is ap rogram that is rexecuting in memory.
		- an executable is a program that resides in the file system.
	- ### Foreground vs background processes.
	  heading:: 3
		- a process is in the foreground when the shell waits for the process to compelte before executing another command typed by the user.
			- You can interact with a foreground process in a shell.
		- A process is in the background when the shell does not wait for the process to complete.
		- How do you stop a foreground process?
			- Control-Z
		- How do you kill a foreground process?
			- CONTROL-C
	- ### Putting a process in the background?
	  heading:: 3
		- A job can be put in the background by initiating the comamnd wit han *&* following it.
		- You can also put a stropped process in the background by using the bg command. IF the job number is not specified, then the most recently stop job is put i nthe background.
		- `bg [%num]`
	- ## Putting a process in the foreground.
	  heading:: 2
		- `fg [%num]`
	- ## Reporting process status
	  heading:: 2
		- the **ps** command orints informaiton about current processes on a mahcine. The process ID (PID) terminal identifier, cumulative exutation time, and command name are given. By default only the processes assoicated with a terminal are show. The PID is guaranteed to be unique among current processes for the processor.
			- `ps [options]`
	- ## Suspending Process
	  heading:: 2
		- A user can suspend a background job or process by using the `stop` command. Either the PID or the job number can be specified as an argument
			- `stop [%num | pid]`
		- A process can suspend itself for a specified amoutn of time by issuing the `sleep` command.
			- `sleep seconds`
	- ## Terminating a process
	  heading:: 2
		- A process can be terminated by using the `kill` command. Either the job number or PID can be specified.
		- General form. One common option is `-9` which represents a signal number representing **SIGKILL** to unconditionally terminate a process.
			- `kill [option] %num ` - kill a process by job number
			- `kill [option] pid`- kill a process by PID
	- ## Top Command.
	  heading:: 2
		- The top command shows the top CPU processes.
	- ## At Command
	  heading:: 2
		- The `at` unix utility reads commands from standar input and groups them together to beexecuted at a specified time.
	-