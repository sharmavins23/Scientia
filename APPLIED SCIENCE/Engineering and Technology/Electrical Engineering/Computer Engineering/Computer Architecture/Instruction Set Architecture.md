An instruction set architecture (ISA) is a model of computation. It can also be seen as a 'plan' for how a computer is designed. A device that executes instructions described by the ISA, such as a [[Central Processing Unit (CPU)]], is also referred to as an implementation.

ISAs generally specify the instructions, data types, registers, and other quirks about the hardware and software and define the [[Instruction Set Architecture#Dynamic-Static Interface|Dynamic-Static Interface]] contract.

Several design choices for ISAs are ultimately trade-offs, such as interactions with the [[Iron Law of Performance and Power]].

## Dynamic-Static Interface (DSI)

A dynamic-static interface, or DSI (also known as the Hardware/Software Interface, or HSI), is the contract that the computer architect and programmer make. Also referred to as the hardware-software interface, or HSI, this contract states what assumptions the programmer may make about the underlying hardware and what the programmer must compensate for.

The DSI and what functionality is embedded within the hardware is a topic of extreme and current debate within many scientific communities, including the security community. For instance, the [[Spectre/Meltdown]] software [[vulnerability]] occurred due to [[Branch Predictors|Branch Predictors]] mechanisms handled within the hardware.

## Assembly Language

An assembly (ASM) language is a [[low-level]] [[programming language]] that directly represents instructions a CPU [[Pipelining (Computation)#Datapath|datapath]] may read. Usually, this language is not meant for humans to write; Rather, a [[compiler]] will compile a [[high-level]] programming language down to assembly, where an [[Instruction Set Architecture#Assembler|assembler]] will convert the assembly down to machine code. The step to create assembly may be skipped entirely, as it is (relatively speaking) unnecessary.

The notion of [[RISC]] and [[CISC]] refer to this - Generally, RISC ISAs will contain fewer instructions, and each instruction will do different things. A CISC ISA will contain more instructions, with each instruction doing several things at once.

### Assembler

An assembler program will convert assembly language into raw binary for a [[Central Processing Unit (CPU)|CPU]] [[Pipelining (Computation)#Datapath|datapath]] by translating human-readable assembly into binary. Usually, these programs are designed as large case statements, though more complicated designs may exist (such as with tables for labels jumping throughout the programs). Usually, assemblers do not apply optimizations to code.