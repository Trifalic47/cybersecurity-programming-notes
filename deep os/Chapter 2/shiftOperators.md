---
id: shiftOperators
aliases: []
tags: []
---
---

# Bitwise Shift Operators

## Overview
Shift operators move bits left or right in a binary number.

---

## Left Shift (<<)

### Concept
*Moves bits to the left. Zeros are filled on the right.*

### Example
5 in binary:
`00000101`

After left shift by 1:
`00001010 = 10`

### Rule
`x << n = x × (2^n)`

### Code
```c
int x = 5;
printf("%d", x << 1); // 10
```
