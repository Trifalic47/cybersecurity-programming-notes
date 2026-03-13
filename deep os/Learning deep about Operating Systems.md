***
The book I am reading through: `Computer Systems: A programmers perspective`
You can download it from [here](https://ia601501.us.archive.org/35/items/informationTechnologyBooks/Bryant_R__O_39_Hallaron_D_-_Computer_Systems_A_Programmer_39_s_Perspective_-_2010.pdf)

![[Pasted image 20260312132055.png]]

# CS:APP Reading Plan

> Computer Systems: A Programmer's Perspective — Bryant & O'Hallaron (2nd Ed.) Goal: Systems foundation for offensive security

---

## Chapters

### Chapter 2 — Data Representation

- Bits, bytes, integers, overflow behavior
- Read it all
- [ ] Done

---

### Chapter 3 — x86-64 Assembly ⭐ MOST IMPORTANT

- Machine-level representation of C programs
- Stack frames, calling conventions, how C looks at the metal
- **Grind this, don't skim. Do every practice problem.**
- Everything in offensive security (buffer overflows, ROP, shellcode) requires fluent assembly reading
- [ ] Done

---

### Chapter 6 — Memory Hierarchy

- Sections 6.1 – 6.4 only
- Cache and locality basics
- [ ] Done

---

### Chapter 7 — Linking

- Sections 7.1 – 7.9
- How ELF binaries are built and linked
- [ ] Done

---

### Chapter 8 — Exceptional Control Flow

- Sections 8.1 – 8.4
- Processes, fork, signals
- [ ] Done

---

### Chapter 9 — Virtual Memory ⭐ SECOND MOST IMPORTANT

- Read it all
- Heap, stack, mmap, how the OS manages a process's address space
- Given the memory allocator project — this will be confirmation, not new material
- [ ] Done

---

## Chapters to Skip (for now)

- Ch. 1 — Intro
- **Ch. 4 — Processor architecture - Read it after you finished above chapters**
- Ch. 5 — Optimizing performance
- Ch. 10 — System-level I/O
- Ch. 11 — Network programming
- Ch. 12 — Concurrent programming

> Networking and I/O come later.

---

## Context

- CS:APP teaches what happens **underneath** C — how code becomes assembly, how the CPU executes it, how the OS manages memory.
- Exploits live in the gap between what C says and what the machine actually does.

---
