---
title: Rudimentary Interpreter
date: 2026-06-12
description: This project page documents my standalone exploration into Abstract Syntax Trees (ASTs) in C. Built as a rapid prototyping sandbox, this repository was where I figured out how to construct dynamic trees for mathematical expressions and translate them into assembly-like instructions before implementing the final architecture in my compiler.
summary: This project page documents my standalone exploration into Abstract Syntax Trees (ASTs) in C. Built as a rapid prototyping sandbox, this repository was where I figured out how to construct dynamic trees for mathematical expressions and translate them into assembly-like instructions before implementing the final architecture in my compiler.
tags:
  - C
  - low-level
  - AST
categories:
  - Programming
  - completed
  - learning
---
## Project Intent

- Master the concept of tree-based syntax representation to overcome previous parsing limitations.
- Learn how to parse mathematical expressions while maintaining proper operator precedence (e.g., multiplication before addition).
- Prototype the translation logic required to flatten a deeply nested tree structure into a linear stream of assembly commands.
- Project has been deemed **successful** as it served its purpose as the direct structural blueprint for the compiler's expression engine.

## System Architecture

### Dynamic AST Sandbox

The prototype implements a basic node-based tree structure built manually in C:

- **Precedence Handling:** Nodes are structured such that lower-precedence operations (like addition) sit higher in the tree, forcing higher-precedence operations (like multiplication) to evaluate first.
- **Recursive Translation:** A tree-walking algorithm traverses the nodes and prints out corresponding assembly-style text commands sequentially.

## Chronological Progress (From Git History)

- **The Beginning:** Started with a barebones implementation to understand basic binary tree structures for expressions.
- **First Milestone (Addition):** Successfully walked the tree to translate simple addition expressions into linear commands, though bytecode generation was omitted.
- **Expanding Scope (Multiplication/Division):** Added complex operations, tackling the math logic required to chain multiple distinct operators together.
- **The Break-Through:** Spent time debugging chained AST nodes to ensure deeply nested operations translated in the correct order without breaking execution paths. _Side note: Reminded myself the hard way why `break` statements are mandatory in C `switch` blocks._

## Limitations

- **No Bytecode Generation:** The project stops at printing textual instruction commands; it does not write actual binary machine code or byte arrays to a file.
- **Strictly Mathematical:** The sandbox only handles arithmetic operations and lacks nodes for variables, logic loops, or conditional statements.

## Project Outcomes

- Successfully figured out the recursive logic needed to translate a multi-layered, chained AST into linear instructions.
- Decoupled expression parsing from execution, permanently moving away from brittle, nested `if` statements.
- **Directly ported this exact translation logic into my main Compiler project to handle its mathematical expression engine.**
- ✘ Failed to implement a memory-cleanup routine for the allocated tree nodes within this sandbox environment.

## Future Plan

none. this is complete. complete in every way possible. it has achieved all intended goals, and was a basic learning project so its done.

---
## Repository
1. https://github.com/rougedroid/BasicASTinC