
> **Project:** Implement a full BST in C using only syscalls and your own allocator.  
> **Constraint:** No `printf`, no `malloc`, no `stdlib.h`. Raw syscalls + `my_malloc` only.

---

## What Is a BST

A Binary Search Tree is a linked structure of nodes where every node holds a value and two pointers — left and right.

**The one rule that defines everything:**

- Left child < Parent
- Right child > Parent

This single rule makes every operation — insert, search, delete — reducible to a decision at each node: go left or go right.

```
Insert: 5 → 3 → 7 → 1 → 6

        5
       / \
      3   7
     /   /
    1   6
```

In C, a node is just:

```c
struct Node {
    int value;
    struct Node *left;
    struct Node *right;
};
```

---

## Operations You Must Implement

| Operation | Difficulty | Notes                              |
| --------- | ---------- | ---------------------------------- |
| `insert`  | Easy       | Recurse until NULL, place node     |
| `search`  | Easy       | Return node or NULL                |
| `inorder` | Easy       | Left → Root → Right, use `write()` |
| `delete`  | Hard       | Three cases — see below            |

### Delete — The Three Cases

1. **Node has no children** → free it, set parent pointer to NULL
2. **Node has one child** → replace node with its child
3. **Node has two children** → find the in-order successor (smallest in right subtree), copy its value into current node, delete the successor

Case 3 is where your pointer logic will break. That's the point.

---

## Man Pages to Read

These are the only ones you need. Read them fully — not skimming.

### Core Syscalls

```
man 2 write      — raw stdout output, replaces printf
man 2 brk        — move the program break (used by your allocator)
man 2 sbrk       — increment the break, returns old break address
man 2 exit       — terminate the process cleanly
```

### C Reference (Section 3 — but acceptable here)

```
man 3 strlen     — only if you write a helper to print ints as strings
```

> You don't even need `strlen` if you write your own `int_to_str` manually. Recommended.

---

## Man Pages to Skip

Do not open these. They will pull you toward lazy habits.

```
man 3 printf     — banned. use write()
man 3 malloc     — banned. use your sbrk allocator
man 3 free       — banned. use your my_free()
man 3 fprintf    — banned.
man 3 memset     — write your own zero-fill loop, 4 lines
man 3 memcpy     — write your own copy loop if needed
man 3 qsort      — irrelevant
man 3 stdlib     — stay away entirely
```

---

## Your Stack for This Project

```
write(2)          → output
sbrk(2) / brk(2) → memory (via your existing allocator)
exit(2)           → program termination
your my_malloc    → node allocation
your my_free      → node deletion
```

---

## Suggested File Structure

```
bst/
├── main.c          — entry point, test cases
├── bst.c           — insert, search, delete, inorder
├── bst.h           — struct Node, function declarations
├── allocator.c     — your my_malloc / my_free (port from old project)
├── allocator.h
└── utils.c         — int_to_str, my_write helpers
```

---

## Build Command

```sh
gcc -Wall -Wextra -std=c11 -o bst main.c bst.c allocator.c
```

No flags to disable warnings. Fix every warning.

---

## Test Cases to Verify Correctness

```
Insert: 10, 5, 15, 3, 7, 12, 20
Inorder expected: 3 5 7 10 12 15 20

Delete 5  (two children) → Inorder: 3 7 10 12 15 20
Delete 3  (leaf)         → Inorder: 7 10 12 15 20
Delete 15 (one child)    → Inorder: 7 10 12 20
```

If your inorder output doesn't match exactly, your delete is broken.

---

## Links

- [[CS:APP]] — Chapter 9 (Virtual Memory) for deeper allocator understanding later
- [[my_malloc]] — Port your allocator from the previous project
- [[PicoCTF]] — Unrelated but don't let this distract you

---

_Read the man pages. Write the code. Don't Google._