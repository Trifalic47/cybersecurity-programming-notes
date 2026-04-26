---
id: Overview
aliases: []
tags: []
---
___

# Aim
#### Making an inerative shell programm using C.

---

# What to use and what not to

*We will use the pure C functions and will not use external libraries like **stdio.h** ,**string.h**. We will use the **syscalls** and only 3libraires -> **unistd.h**,**signal.h** and **sys/wait.h***

##### concepts used

	Firstly we should know about the pointers,memory allocation,heap,stack,including custom files,process IDs(pid),processes,file descriptors(fd) and 2d Arrays. Rest of the concept  we will learn while making shell program.

> [!note] Requirements
> You should be on the linux or mac os.This programm does not work on the windows becuase syscalls for the windows are different
##### Banned things

- External ease libraries like **stdio.h**,**string.h** -> Make your own print function to print statements using syscalls -> read and write
- Using **malloc** and **free**

---

# Functionalities

- Could run shell commands like ls,mkdir,cd,touch etc.
- Compaitable using pipes
- Handle commands by making child process using fork

> [!note] You could read the man pages to read the documentation of function
> **Example->** *man 2 fork*,*man 2 read* etc.

---

# Lets jump in

[[Basic Functions|Proceed]]
