Single instruction, multiple data stream (SIMD) is a type of parallel computing in [[Flynn's Taxonomy]] describing computers with multiple processing elements that perform the same operation on multiple data-points simultaneously. SIMD can be internal to the hardware's design, and it can be accessible through [[Instruction Set Architecture|instructions]], but it is not its own ISA.

A simple example is within modern CPUs - Modern registers contain wide registers (e.g. 256-bit registers within [[Advanced Vector Extensions]] for [[x86 Assembly|the x86 ISA]]). This data can be packed into wider registers and processed in one singular instruction.

# Worked Example

Suppose we have the following [[C++]] program to encode an extremely long string under the [[ROT13]] [[Cipher|cipher]]:

```cpp
void rot13_naive(char *data, size_t len) {
	// Iterate over all characters
	for (size_t i = 0; i < len; i++) {
		// Skip if the character is 
	}
}
```

This code iterates through all of the individual characters. For each character, it performs the following processing:
- Is the character between `a` and `z`?
- If so, 'rotate' the character by adding 13 to its [[ASCII]] value. Using modular arithmetic (and a sum of the initial value), shift the character back to within `a` to `z`.

You can use [[C++ Intrinsics]] to 