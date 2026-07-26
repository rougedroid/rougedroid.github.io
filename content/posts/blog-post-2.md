---
title: "Story of a Comeback : The working Compiler in C"
date: 2026-07-26
publishdate: 2026-07-26
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

#### A magnificent side quest

After finishing the lexer, I moved onto making the core of a compiler. The block of code that actually translates a stream of tokens from source code into the required Assembly/Binary code to be ran on the machine. 

Here, learning from my mistakes in the Interpreter, i started tinkering with an AST for the mathematical expressions. I wrote multiple supporting functions to try and plug them into a master function, together with which it would be able to create and execute AST's from tokens. But these attempts were in vain as I ended up scrapping everything here, since I realised I didn't **ACTUALLYY** understand how an AST was useful for program execution. 

This is where i abandoned the Compiler project for a few days to completely focus on implementation of an AST on a blank sheet, without having to make it co exist with my token arrays or other parts of my compiler. I used the trusty ol' ChatGPT as a mentor to learn it by building small parts of it at a time. 

AST's were really marvellous for my then inexperienced brain, I was completely blown away by the fact that the AST tree is called top down, BUT the execution happens BOTTOM UP. This was fascinating then, but looking back, its just elegant design. 

#### The pitfall

While learning AST implementation, I focused only on arithmatic aspect of it, a.k.a. operator precedence and bracket precedence. Unfortunately, a compiler has to deal with more types of tokens, I completely forgot about logical and control statements. At this point, my compiler was a glorified calculator. 

Since the AST was already written by this point, i decided to implement the logical statements and comparison operators using the good old `if-else` statements. It did end up working by the end, except it left me with more syntax constraints than before. Now, the syntax for and if condition was : `if ( exppr1 ; = exppr2 ; ) { if block };` yeah..... the semi-colons in the conditional statement are compulsory. 

#### What am I working on now? 

After somewhat mastering low level C code, and working with registers and pure pointer horrors, I have decided to take a leap into the unknown magical powers of Analog Electronics. I have been working on building a High-End peripheral oscilloscope which includes extensive analog electronics and teaches me micro-controllers as well. I call this High-end because I am targeting a 10 million samples per second, allowing me to sample signals upto 1Mhz clearly. And an absolutely wild range of +-10mV to +-15V of signal range that can be recorded. And this also uses a bare-bones STM32H723 chip, no dev boards for me. Wish me luck!!!






