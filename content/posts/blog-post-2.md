---
title: "Story of a Comeback : The working Compiler in C"
date: 2026-07-26
publishdate: 2026-07-27
---
After the failed interpreter, and then swiftly followed by a brutal JEE, I started work on my compiler on the 3rd of June, this time more determined, and armed with the knowledge of a Failed Interpreter and building a custom VM from scratch. 

> [!Context]
> Work on the VM was started on 27th May. This is a very basic VM, it uses a Von-Neumann Architecture, and it was built for logic testing, rather than a real simulation. And hence, it lacks clock cycles, and actual microprocessor like processing. 
> The VM has a "RAM" of 131kB and executes a custom 16-bit instruction set. 
> Other instructions can be found on the related [Project Page](https://rougedroid.github.io/projects/compiler-vm/)
> 

#### Remnants of the past

I almost directly copied the token data structures from my failed interpreter since they were a very effective way to store and process the tokens, although not so efficient for manipulating the token array once the tokens have been stored from the source code. 

There was also a much stricter syntax regulation to make the job of the lexer easy since my main objective with the project was to understand how compilers work, and at the time I had no interest in writing a robust lexer from scratch. ( I made it a requirement to write every functional part of the compiler from scratch, only using standard C libraries for I/O and data manipulation. )

#### 

