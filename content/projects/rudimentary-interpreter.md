---
title: Rudimentary Interpreter
date: 2026-04-06
description: This project page details my initial, highly experimental attempt at building a rudimentary interpreter from scratch in C. Designed as a foundational learning experiment to understand the mechanics of parsing and execution, this project served as a critical stepping stone—and a masterclass in architectural mistakes—before the development of my subsequent, fully functional compiler.
summary: This project page details my initial, highly experimental attempt at building a rudimentary interpreter from scratch in C. Designed as a foundational learning experiment to understand the mechanics of parsing and execution, this project served as a critical stepping stone—and a masterclass in architectural mistakes—before the development of my subsequent, fully functional compiler.
tags:
  - C
  - low-level
  - interpreter
categories:
  - Programming
  - abandoned
---
## Project Intent

- Understand how interpreters and compilers actually work under the hood.
- Learn the mechanics of lexers, parsers, and execution engines by building them manually.
- Implement a basic text-to-execution pipeline in pure C without relying on existing parser tools.
- Project has been deemed **archived/incomplete** as a standalone tool, but highly successful as a foundational learning vehicle that directly enabled my later compiler project.

## System Architecture

### Monolithic Pipeline

The initial architecture attempted to process code in a single, continuous chain of instructions rather than utilising decoupled stages:

- **Token-Processor Hybrid:** The system attempted to tokenise text, clean up white-spaces, delete processed tokens, and execute logic all within the same execution loop.
- **String-Heavy Analysis:** The interpreter relied heavily on manual string manipulation and destructive array operations in C to modify the source code at runtime.

## Limitations

### Lexer

- **Token Separation Failure:** The lexer was unable to reliably detect token boundaries.
- It relied on rudimentary, brittle nested `if` statements to guess boundaries rather than employing a strict, multi-step splitting and analysis framework.

### Parser & Processor

- **The "AST" Wall:** The project completely lacked an Abstract Syntax Tree (AST). It attempted to evaluate complex, nested code syntax using increasingly messy nested `if` statements, which repeatedly broke down under complexity.
- **Destructive Memory Management:** The processor tried to physically delete tokens and wipe whitespaces out of memory on the fly during the parsing phase, resulting in incredibly messy, bug-prone C pointer logic.

## Project Outcomes

- Deeply understood the absolute necessity of separating Lexing, Parsing, and Execution into distinct, isolated phases.
- Learnt firsthand why Abstract Syntax Trees (ASTs) are mandatory for language syntax evaluation.
- **Directly applied these brutal lessons to my later compiler project, which I successfully completed as a result. (which also lacks gc and memory management)**
- ✘ Failed to build a working interpreter execution engine due to code complexity collapse.
- ✘ Failed to implement any form of memory management or garbage collection.

## Future Plan

I am explicitly planning on writing a brand-new interpreter from scratch in C to finish what I started, using a highly disciplined approach:

- **Strict Lexer & Parser:** The new lexer will be just as strict as my successful compiler. I don't care about complex string-processing edge cases; the goal is to understand code internals, not build a text editor.
- **Garbage Collection (GC):** I will implement a robust garbage collection system in this new interpreter. Because my successful compiler currently lacks all forms of optimisation (including a GC), I will use the new interpreter as a testing ground to master GC mechanics before back-porting it to the compiler.

---
## Repository
( WARNING: DANGEROUSLY HORRIBLE CODE BELOW )
- i warned you....... https://github.com/rougedroid/Rudimentary-Interpreter