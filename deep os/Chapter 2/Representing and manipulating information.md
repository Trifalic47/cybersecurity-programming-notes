***

![[Pasted image 20260313140845.png]]


*Modern computers store and process information represented as 2-valued signals*

***

## **Three most important representations of numbers**

*We consider the three most important representations of numbers. **Unsigned***
***encodings** are based on traditional binary notation, representing numbers greater*
*than or equal to 0. Two’s-complement encodings are the most common way to*
*represent **signed integers**, that is, numbers that may be either positive or neg-*
*ative. **Floating-point encodings** are a base-two version of scientific notation for*
*representing real numbers*

***

*The computers use binary representations to encode numeric values.*

## `e` notation
*The `e` notation is used to give power to 10. For example 2e2.
2e2 means = 2 x 10<sup>2</sup> - 2 x 100 - 200
*

***

## Virtual Memories

*Every programm got its own virtual memory which lives in RAM.It means Virtual Memory is a place where the programm runs. And the `stack` and `heap` lives in the virtual memory.But one surprising thing is that programms think that they got full access to the RAM but the reality is they live in small part of ram.*

***

## Bits and bytes

*I am sure that you know about bit and bytes but I am going to tell you something memory allocation of different data types*

- int - **4bytes**
- char - **1byte**
- size_t - **8bytes**

***There are many more you can find out about it online***

***

*A byte can hold numbers till 00000000<sub>2</sub> - 11111111<sub>2</sub> which are equal to `255`.*

***

## Converting decimal into binary

```mermaid
flowchart TD
    A[Start with decimal number] --> B[Divide by 2]
    B --> C[Note the remainder 0 or 1]
    C --> D{Is quotient 0?}
    D -- No --> E[Quotient becomes new number]
    E --> B
    D -- Yes --> F[Read remainders bottom to top]
    F --> G[That is your binary number]
```

#### For example
```
13 ÷ 2 = 6  remainder 1  ← last digit
6  ÷ 2 = 3  remainder 0
3  ÷ 2 = 1  remainder 1
1  ÷ 2 = 0  remainder 1  ← first digit

Final Result -> 1011
```

***

### Hex to binary

*Hexdecimal consists of 0-9 and a-f. Which are 16total and hence its called base16.The memory address of an variable in ram is also an hexadecimal which looks like `0x353af`.
Here `0x` contributes 0 bytes , `0x`,it just sets prefix that next elements will be hexadecimals.*
***One hex -> 4bits/A half bit***

```mermaid
flowchart TD
    A[Start with hex number] --> B[Take one hex digit]
    B --> C[Convert letter to decimal if A-F]
    C --> D[Divide by 2, note remainder]
    D --> E{Is quotient 0?}
    E -- No --> F[Quotient becomes new number]
    F --> D
    E -- Yes --> G[Read remainders bottom to top]
    G --> H[Pad to 4 bits with leading zeros]
    H --> I{More hex digits?}
    I -- Yes --> B
    I -- No --> J[Concatenate all 4 bit groups]
    J --> K[That is your binary number]
```


#### Example

## Hex to Binary — 0xAF

**Step 1 — Take one hex digit at a time**
Start with **A** → convert to decimal → A = 10

**Step 2 — Convert A to binary**

| Division | Quotient | Remainder |
|----------|----------|-----------|
| 10 ÷ 2 | 5 | 0 |
| 5 ÷ 2 | 2 | 1 |
| 2 ÷ 2 | 1 | 0 |
| 1 ÷ 2 | 0 | 1 |

Read remainders bottom to top → pad to 4 bits → **1010**

**Step 3 — Convert F to binary**
F → 15 in decimal

| Division | Quotient | Remainder |
|----------|----------|-----------|
| 15 ÷ 2 | 7 | 1 |
| 7 ÷ 2 | 3 | 1 |
| 3 ÷ 2 | 1 | 1 |
| 1 ÷ 2 | 0 | 1 |

Read remainders bottom to top → **1111**

**Step 4 — Concatenate**

| Hex | A | F |
|-----|------|------|
| Binary | 1010 | 1111 |

**Result: 10101111**

***

## Converting decimal to hex 

*Decimals are our base10(0-9).So to convert decimal into hex/base16 we have to divide from 16*

```mermaid
flowchart TD
    A[Start with decimal number] --> B[Divide by 16]
    B --> C[Note the remainder]
    C --> D{Is remainder 10 or above?}
    D -- Yes --> E[Convert to letter A=10 B=11 C=12 D=13 E=14 F=15]
    D -- No --> F[Keep as digit]
    E --> G{Is quotient 0?}
    F --> G
    G -- No --> H[Quotient becomes new number]
    H --> B
    G -- Yes --> I[Read remainders bottom to top]
    I --> J[That is your hex number]
```


#### Decimal to Hex — Example: 219

**Step 1 — Divide by 16**

| Division | Quotient | Remainder | Hex Digit |
|----------|----------|-----------|-----------|
| 219 ÷ 16 | 13 | 11 | B |
| 13 ÷ 16 | 0 | 13 | D |

> Quotient hit 0 — stop.

**Step 2 — Read remainders bottom to top**

| Order | Remainder | Hex Digit |
|-------|-----------|-----------|
| First | 13 | D |
| Last | 11 | B |

**Result: 0xDB**

> 💡 Only remainders 10 and above get converted to letters A-F. The rest stay as digits.