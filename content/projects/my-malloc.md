---
title: Custom malloc Implementation
date: 2026-05-27
description: This project page details a functional, custom implementation of the dynamic memory allocation functions my_malloc and my_free built in C. The allocator directly requests memory from the kernel using anonymous memory mappings (mmap) and manages allocated blocks via a sequential, padded linked-list metadata tracking system.
summary: This project page details a functional, custom implementation of the dynamic memory allocation functions my_malloc and my_free built in C. The allocator directly requests memory from the kernel using anonymous memory mappings (mmap) and manages allocated blocks via a sequential, padded linked-list metadata tracking system.
tags:
  - C
  - low-level
  - memory-management
categories:
  - Programming
  - completed
---
## Project Intent

- Understand how memory allocation systems (`malloc`, `free`) map user-space requests to kernel-allocated memory blocks.
- Gain a deep understanding of memory alignment, block padding, and metadata overhead calculations in pure C.
- Implement a foundational block-splitting and chunk-coalescing mechanism to reuse freed memory spaces.
- Project has been deemed **successful and complete**, operating as a working barebones alternative to standard library allocators.

## System Architecture

### Linked-List Metadata Tracking

The allocator tracks allocations linearly by embedding structural headers directly into the memory space immediately preceding the usable data pointer:

- **Block Header Setup:** Each block begins with a 16-byte aligned `block_header_t` struct containing the block size, a boolean tracking its availability (`is_free`), and a pointer to the next block.
- **Kernel Mapping (`mmap`):** Rather than adjusting the heap break pointer (`sbrk`), this implementation bypasses the standard heap pool entirely, requesting page-aligned maps directly via `mmap` with flags `MAP_PRIVATE | MAP_ANONYMOUS`.
- **Pointer Arithmetic Alignment:** The user is always handed a data pointer offset by exactly `+1` block-header unit (16 bytes) past the metadata struct (`cblock + 1`).

### Performance & Time Complexity

- **Allocation / Deallocation Complexity:** $\mathcal{O}(N)$. Finding a free slot or validating a block address requires iterating sequentially across the explicit `chain_length` list of nodes.
    

## Limitations

### Performance and Scale

- **$\mathcal{O}(N)$ Search Overhead:** Because it utilizes a single continuous linked list, allocations must parse every previous block to locate an existing free chunk, which severely limits high-throughput scaling.
- **Brittle Pointer Stepping:** The current logic increments blocks heavily through raw struct pointer offsets (e.g., `cblock + (reqsize / sizeof(*cblock))`), which can fall prey to subtle tracking bugs if the initial requested allocation size isn't a flawless multiple of the struct size.

### Fragment Cleanups

- **Limited Coalescing Window:** The current merging algorithm in `my_free` simplifies the coalescing phase by stepping forward over the tracked chain, but does not deeply collapse multiple non-contiguous free spaces or release completely empty pages back to the kernel using `munmap`.

## Project Outcomes

- Successfully designed an working allocation layer in C that executes real memory binding without crashing standard operational systems.
- Decoded the intricate pointer math required to compute strict byte padding ($8 \times \frac{\text{rsize} + \text{sizeof(header)} + 7}{8}$).
- Understood how `malloc` payloads store their metadata silently "behind" the pointer returned to the developer.
- ✘ Failed to implement standard memory-efficiency algorithms like segregated free lists, Best-Fit, or segregated buddy allocation systems.

## Future Plan

If I revisit low-level memory tracking, I will rewrite this allocator to utilize an asymmetric **Segregated Free List** structure backed by a balanced tree (like a Red-Black tree) to lower lookup bounds from $\mathcal{O}(N)$ to $\mathcal{O}(\log N)$.

Additionally, I plan to integrate proper kernel page reclaiming via `munmap` so that when large, sequential blocks are freed, memory is immediately and systematically handed back to the OS.

---
## Repository
1. https://github.com/rougedroid/My-Malloc-Implementation/