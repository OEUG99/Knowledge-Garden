-
- An assembler program creates object code by translating combinations of mnemonics and syntax for operations and addressing modes into their numerical equivalents.  This representation typically includes an operation code (opcode) as well as other control bits and data. [(via Wikipedia)](https://en.wikipedia.org/wiki/Assembly_language#Assembler)
- Assemblers are essentially a [Compiler]([]) that translates assembly code into machine code.
- # Types of Assemblers
	- **One-pass Assembler** – This type of assembler process the assembly code into machine code all within 1 go.
	- **Multi-Pass Assembler** –  This type of assembler processes assembly code in multiple passes/phases.
		- **Analysis Phase (Phase 1):**
			- This is the initial phase where the source code is read line by line from an input file, analyzing the structure of each instruction.
			  
			  An intermediate File is then created, each line read from the source program is converted into an intermediate form and written to the intermediate file. The intermediate form is as follows... each line consists of the location counter value, the opcode mnemonics, and the operand (if any exists).
			  
			  The opcode mnemonics can be found with in the assemblers predefined table that contains all the opcode mnemonics and their equivalent machine codes.  This table is called the Opcode table or OPTAB for short
			  
			  Every time a label is found in the source code, it is added to the SYMTAB (Symbol Table), along with its value or address.
			  
			  If the source code contains constants or literals, the assembler handles them during this phase. Constants get converted into their respective binary values or hexadecimal values, while literals get stored separately and are processed at the end of the source code. 
			  
			  The assembler also evaluated assembler directives during this phases. directives are instructions that guide the assembly process (like specifying the start address or defining data elements, etc.)
		- **Synthesis Phase (Phase 2):**
			- During this phase, the assembler uses the intermediate file to produce the actual machine language code.
			  
			  The assembler reads instructions from the Intermediate file, translates each opcode mnemonic into its corresponding machine language opcode (using OPTAB), and writes the resulting machine instructions to the object code file.
			  
			  The assembler replaces the symbolic operands with their actual addresses. The addresses of the symbolic operands are found in SYMTAB that was generated during Phase 1. 
			  
			  The assembler calculates the relative addresses for branch instructions or jumps. The relative  address is calculated by subtracting the address of the next instruction (location counter value after the instruction is stored) from the target address.
			  
			  The assembler encodes each instruction into machine-readable form. For example, a "LOAD" instruction  will be encoded into a specific number that represents "LOAD in the machine language.
			  
			  If the source program is meant to produce relocatable code, the assembler will also generate a relocation bit for each word of the object program. The
	-