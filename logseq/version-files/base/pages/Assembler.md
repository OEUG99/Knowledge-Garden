-
- An assembler program creates object code by translating combinations of mnemonics and syntax for operations and addressing modes into their numerical equivalents.  This representation typically includes an operation code (opcode) as well as other control bits and data. [(via Wikipedia)](https://en.wikipedia.org/wiki/Assembly_language#Assembler)
- Assemblers are essentially a [Compiler]([]) that translates assembly code into machine code.
- # Types of Assemblers
	- **One-pass Assembler** – This type of assembler process the assembly code into machine code all within 1 go.
	- **Multi-Pass Assembler** –  This type of assembler processes assembly code in multiple passes/phases.
		- **Analysis Phase (Phase 1):** 
		  
		  This is the initial phase where the source code is read line by line from an input file, analyzing the structure of each instruction.
		  
		  An intermediate File is then created, each line read from the source program is converted into an intermediate form and written to the intermediate file. The intermediate form is as follows... each line consists of the location counter value, the opcode mnemonics, and the operand (if any exists).
		  
		  The opcode mnemonics can be found with in the assemblers predefined table that contains all the opcode mnemonics and their equivalent machine codes. 
		  
		  Every time a label is found in the source code, it is added to the SYMTAB (Symbol Table), along with its value or address.
	-
	-