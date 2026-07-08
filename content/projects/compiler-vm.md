---
title: Custom Compiler-VM Bundle
date: 2026-06-16
description: This project page looks at some of the technical details regarding my implementation of a custom compiler and a VM for a simple, custom ISA. This project is built in C and the vm follows a von Neumann Architecture and is register based.
summary: This project page looks at some of the technical details regarding my implementation of a custom compiler and a VM for a simple, custom ISA. The project is built in C and the vm follows a von Neumann Architecture and is register based.
tags:
  - C
  - low-level
  - compiler
categories:
  - Programming
  - completed
---
## Project Intent
- Understand the working principle of micro controllers at the lowest level of software
-  Gain a better understanding of register based systems and how memory is managed
- Understand the mechanism for jumps, conditional statements and other program control statements
- Understanding translation from a high level language to assembly code in regular systems
- Understanding and implementing compiler optimisations  

 Project has been deemed successful as of 18th June since achieves a majority of the intents listed.

---
## System Architecture
### Address Spaces
- The current system uses a 16 bit long address space. Each address refers to a word ( 2 bytes )
- Effective available memory is around 131 KB

### Instruction Set Specifications
- This project implements a custom instruction set which has fixed length for data and instructions. 
- Each instruction and value ( only integer value ) is 2 bytes long. 
- The instruction set evolved along with the compiler as there was no separate planning stage for the instruction set, and hence, there are a few flaws that will be rectified in future versions. 

### Compiler Architecture
- The compiler uses a hybrid system combining a dynamic Abstract Syntax Tree for mathematical expression and ensuring precedence and a rigid if statements to process keywords in the language. 
- This choice was made since the custom language includes a very small number of keywords and hence, the if block was faster for development and execution and skipping it did not skip any part of the intent of doing this project. 


### Limitations
#### Compiler
- The compiler lacks rigorous grammar parsing and has led to the requirement of bizarre syntax in certain situations. Eg.
	1. If statements must also have an else block
	2. Each expression must end with a ";" even within if/while statements. Syntax: 
		- if ( 1; == 2; ) { .... } else { .... }
- Uses rigid if statements to process keywords, this is not scallable and will need redesigning in future.
- Does not support functions or input during runtime. 
#### Instruction Set/VM architecture
- The instruction set and the VM impose very "weird" rules, such as a fixed register for the result of an addition, and a different fixed register for each of the arithmetic operations. 

---
## Project Outcomes
- [x] Understood the register based architecture deeply including program control statements' inner working
- [x] Understood the steps and mechanisms involved in converting a high level language into a low level instruction set
- [x] Learnt to create and use ASTs
- ✘ Failed to understand Compiler optimisations as none were implemented in v1
- ✘ Failed to understand Stack based machines as v1 uses a register based system

---
## Future Plan
- I am planning on returning to this project in college and fixing most of the limitations listed out here. But this system will remain a register based system. 
- A different project will be announced in due time where I will attempt to replicate a real chip with all the CPU clock cycles and the stack framework and real opcodes etc ...
---
## Repositories
1. Compiler: https://github.com/rougedroid/bytecodeCompiler
2. VM: https://github.com/rougedroid/bytecodeVM
