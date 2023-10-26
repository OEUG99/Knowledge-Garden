tags:: #[[Virtual Machines]] #Emulation #Interpreter #Assembler

- # CHIP-8 Emulator and Assembler
	- This project began as a personal exploration into the captivating world of emulation - a field of computing that blends low-level computer architecture with intricate operations. Through my love of retro video games, the idea of creating a CHIP-8 Emulator and Assembler took root. CHIP-8, with its accessible design and manageable complexity, proved to be an ideal entry point for this emulation adventure.
	- ## The History of CHIP-8
		- The CHIP-8 is what is commonly described as a "fantasy console". It is not a physical machine, rather a conceptual virtual machine created in the mind of microcomputer researcher Joseph Weisbecker in the mid 1970s, and its aim was to simplify video game programming on early microcomputers, by providing consistency over a range of differing hardware.
			- The specification for [[Chip-8]] can be found in my dedicate page for it.
		- The use of CHIP-8 has continued well into the 21st century, with modern programming contests and game jams often featuring CHIP-8 categories. Classes on operating system design and embedded systems often use CHIP-8 due to its simplicity yet broad scope in understanding the basics of system design.
	- ## Project's Structure
		- This project had three distinct phases. Each proceeding phase has built on top of the previous stage, adding more complexity to the overall scope of the project.
		- The stages are as followed:
			- **Stage 1 -  The Emulator:**
				- The heart of the project took the form of an interpreter for the CHIP-8 language. It entailed a deep dive into the inner workings of the CHIP-8 system to read, decode, and execute CHIP-8 program instructions accurately. This stage involved an in-depth exploration of computer architecture, reiterating the fundamentals of bitwise operations, which stood as an integral part of the Emulator's operation.
			- **Stage 2 - The Assembler: **
				- During this stage, I created an assembler which is a program that transforms human-readable CHIP-8 assembly code into a structure that our emulator could process. This proved to be a fantastic practical exercise in understanding the translation from higher-level, readable assembly code into machine-level instructions.
				- Through this stage I learned...
					- TODO write this when I get to this stage.
			- **Stage 3 - Game Design: **
				- In this final phase, I put both my emulator and assembler to the test by designing a of my own. This stage not only served as validation for the work done in the previous stages but also yielded a fun, playable game as the end product of the exploration.
				- This was by far the hardest stage, not because it requires both my emulator and assembler to be perfect, rather because I had to program the game in assembly.  As a result, I had to learn how balance memory management while also designing something fun and feasible for 8-bit retro limit