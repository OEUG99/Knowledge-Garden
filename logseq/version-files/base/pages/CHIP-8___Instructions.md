# Standard Chip-8 Instructions
	- ## `0nnn` – SYS addr
		- Jump to a machine code routine at `nnn`.
		- This instruction is only used on the old computers on which Chip-8 was originally implemented. It is ignored by modern interpreters.
	- ## `00E0` – CLS
		- Clear the display.
	- ## `00EE` – RET
		- Return from a subroutine.
		- The interpreter sets the program counter to the address at the top of the stack, then subtracts 1 from the stack pointer.
	- ## `1nnn` – JP addr
		- Jump to location `nnn`.
		- The interpreter sets the program counter to `nnn`.
	- ## `2nnn` – CALL addr
		- Call subroutine at `nnn`.
		- The interpreter increments the stack pointer, then puts the current PC on the top of the stack. The PC is then set to `nnn`.
	- ## `3xkk` – SE Vx, byte
		- Skip next instruction if Vx = `kk`.
		- The interpreter compares register Vx to `kk`, and if they are equal, increments the program counter by 2.
	- ## `4xkk` – SNE Vx, byte
		- Skip next instruction if Vx != `kk`.
		- The interpreter compares register Vx to `kk`, and if they are not equal, increments the program counter by 2.
	- ## `5xy0` – SE Vx, Vy
		- Skip next instruction if Vx = Vy.
		- The interpreter compares register Vx to register Vy, and if they are equal, increments the program counter by 2.
	- ## `6xkk` – LD Vx, byte
		- Set Vx = `kk`.
		- The interpreter puts the value `kk` into register Vx.
	- ## `7xkk` – ADD Vx, byte
		- Set Vx = Vx + `kk`.
		- Adds the value `kk` to the value of register Vx, then stores the result in Vx.
	- ## `8xy0` – LD Vx, Vy
		- Set Vx = Vy.
		- Stores the value of register Vy in register Vx.
	- ## `8xy1` – OR Vx, Vy
		- Set Vx = Vx OR Vy.
		- Performs a bitwise OR on the values of Vx and Vy, then stores the result in Vx. A bitwise OR compares the corresponding bits from two values, and if either bit is `1`, then the same bit in the result is also `1`. Otherwise, it is `0`.
	- ## `8xy2` – AND Vx, Vy
		- Set Vx = Vx AND Vy.
		- Performs a bitwise AND on the values of Vx and Vy, then stores the result in Vx. A bitwise AND compares the corresponding bits from two values, and if both bits are `1`, then the same bit in the result is also `1`. Otherwise, it is `0`.
	- ## `8xy3` – XOR Vx, Vy
		- Set Vx = Vx XOR Vy.
		- Performs a bitwise exclusive OR on the values of Vx and Vy, then stores the result in Vx. An exclusive OR compares the corresponding bits from two values, and if the bits are not both the same, then the corresponding bit in the result is set to `1`. Otherwise, it is `0`.
	- ## `8xy4` – ADD Vx, Vy
	  id:: 653ff75e-9e93-4f74-acea-e27b246b7520
		- Set Vx = Vx + Vy, set VF = carry.
		- The values of Vx and Vy are added together. If the result is greater than 8 bits (i.e., > `255`), VF is set to `1`, otherwise `0`. Only the lowest 8 bits of the result are kept, and stored in Vx.
		- NOTE:  When adding Vx to Vy you need to deal with overflows. One way of dealing with these is to use a bitmask of `0xFF` on the results to get only the lowest 8 bits.  Another more cheeky way, is to cast Vx and Vy to `int16` do the operation then cast back to `int8`.
	- ## `8xy5` – SUB Vx, Vy
		- Set Vx = Vx - Vy, set VF = NOT borrow.
		- If Vx > Vy, then VF is set to `1`, otherwise `0`. Then Vy is subtracted from Vx, and the results stored in Vx.
		- NOTE:  When subtracting Vx and Vy, you will need to deal with overflows similarly to how ((653ff75e-9e93-4f74-acea-e27b246b7520)) needs to handle them. See that opcode for more details.
	- ## `8xy6` – SHR Vx {, Vy}
		- Set Vx = Vx SHR `1`.
		- If the least-significant bit of Vx is `1`, then VF is set to `1`, otherwise `0`. Then Vx is divided by `2`.
	- ## `8xy7` – SUBN Vx, Vy
		- Set Vx = Vy - Vx, set VF = NOT borrow.
		- If Vy > Vx, then VF is set to `1`, otherwise `0`. Then Vx is subtracted from Vy, and the results stored in Vx.
	- ## `8xyE` – SHL Vx {, Vy}
		- Set Vx = Vx SHL `1`.
		- If the most-significant bit of Vx is `1`, then VF is set to `1`, otherwise to `0`. Then Vx is multiplied by `2`.
		- NOTE: You can find the MSB by doing a bitmask with `0x80` on Vx. You can multiply by 2 by shifting Vx by 1.
	- ## `9xy0` – SNE Vx, Vy
		- Skip next instruction if Vx != Vy.
		- The values of Vx and Vy are compared, and if they are not equal, the program counter is increased by `2`.
	- ## `Annn` – LD I, addr
		- Set I = `nnn`.
		- The value of register I is set to `nnn`.
	- ## `Bnnn` – JP V0, addr
		- Jump to location `nnn` + V0.
		- The program counter is set to `nnn` plus the value of V0.
	- ## `Cxkk` – RND Vx, byte
		- Set Vx = random byte AND `kk`.
		- The interpreter generates a random number from `0` to `255`, which is then ANDed with the value `kk`. The results are stored in Vx.
	- ## `Dxyn` – DRW Vx, Vy, nibble
		- Display n-byte sprite starting at memory location I at (Vx, Vy), set VF = collision.
		- The interpreter reads `n` bytes from memory, starting at the address stored in I. These bytes are then displayed as sprites on screen at coordinates (Vx, Vy). Sprites are XORed onto the existing screen. If this causes any pixels to be erased, VF is set to `1`, otherwise it is set to `0`.
		- NOTE: Sprites are represented as a sequence of bytes, where each bit in a byte represents a pixel. Sprites may be up to 16 bytes, for a possible sprite size of 8x15.  Sprites are always 8 pixel wide, however their height can vary. Sprites are stored in memory in a 1-dimensional array, where each pixel is an element in the array. Each pixel is represented in a boolean state `0` for off, `1` for on. In this opcode, you must unwrap the array in the sense that you need to find what row and column a pixel is on.
			- If you are having trouble unwrapping the sprite array, think of it like this, you could convert the 1d-array into a 2d-array with an x and y axis. Converting it into a 2d-array is a very similar problem, as you must find the x, y coordinates to insert each original element into; however, instead of inserting into a 2d array you use these x, y coordinates to set on or off a pixel and just iterate through all the pixels.
	- ## `Ex9E` – SKP Vx
		- Skip next instruction if key with the value of Vx is pressed.
		- Checks the keyboard, and if the key corresponding to the value of Vx is currently in the down position, PC is increased by `2`.
	- ## `ExA1` – SKNP Vx
		- Skip next instruction if key with the value of Vx is not pressed.
		- Checks the keyboard, and if the key corresponding to the value of Vx is currently in the up position, PC is increased by `2`.
	- ## `Fx07` – LD Vx, DT
		- Set Vx = delay timer value.
		- The value of DT is placed into Vx.
	- ## `Fx0A` – LD Vx, K
		- Wait for a key press, store the value of the key in Vx.
		- All execution stops until a key is pressed, then the value of that key is stored in Vx.
	- ## `Fx15` – LD DT, Vx
		- Set delay timer = Vx.
		- DT is set equal to the value of Vx.
	- ## `Fx18` – LD ST, Vx
		- Set sound timer = Vx.
		- ST is set equal to the value of Vx.
	- ## `Fx1E` – ADD I, Vx
		- Set I = I + Vx.
		- The values of I and Vx are added, and the results are stored in I.
	- ## `Fx29` – LD F, Vx
		- Set I = location of sprite for digit Vx.
		- The value of I is set to the location for the hexadecimal sprite corresponding to the value of Vx.
	- ## `Fx33` – LD B, Vx
		- Store BCD representation of Vx in memory locations I, I+1, and I+2.
		- The interpreter takes the decimal value of Vx, and places the hundreds digit in memory at location in I, the tens digit at location I+1, and the ones digit at location I+2.
		- NOTE: Floor division (also known as integer division -- `//`) and modulus is quite useful for implementing this operator. You can take advantage of modulus's remainder to extract terms you desire, and you can take advantage of floor division by shifting numbers to make modulus easier.
			- Example: psuedo-code 
			  ```
			  # Any positive integer. 
			  num = 567 = 567
			  
			  # finds the 100th place:
			  floor(num / 100) = 5
			  
			  # finds the 10s place:
			  floor(num / 10) mod 10 = 6
			  
			  # finds the 1s place:
			  num mod 10 = 7
			  ```
	- ## `Fx55` – LD [I], Vx
		- Store registers V0 through Vx in memory starting at location I.
		- The interpreter copies the values of registers V0 through Vx into memory, starting at the address in I.
	- ## `Fx65` – LD Vx, [I]
		- Read registers V0 through Vx from memory starting at location I.
		- The interpreter reads values from memory starting at location I into registers V0 through Vx.