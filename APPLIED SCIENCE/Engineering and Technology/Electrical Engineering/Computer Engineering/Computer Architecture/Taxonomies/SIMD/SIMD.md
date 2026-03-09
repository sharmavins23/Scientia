Single instruction, multiple data stream (SIMD) is a type of parallel computing in [[Flynn's Taxonomy]] describing computers with multiple processing elements that perform the same operation on multiple data-points simultaneously. SIMD can be internal to the hardware's design, and it can be accessible through [[Instruction Set Architecture|instructions]], but it is not its own ISA.

A simple example is within modern CPUs - Modern registers contain wide registers (e.g. 256-bit registers within [[Advanced Vector Extensions]] for [[x86 Assembly|the x86 ISA]]). This data can be packed into wider registers and processed in one singular instruction.


## Worked example

Suppose we have the following [[C++]] program to convert