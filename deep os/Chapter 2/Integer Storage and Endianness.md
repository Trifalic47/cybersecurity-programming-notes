
---

## Data Sizes

| C Declaration   | 32-bit | 64-bit |
| --------------- | ------ | ------ |
| `char`          | 1      | 1      |
| `short int`     | 2      | 2      |
| `int`           | 4      | 4      |
| `long int`      | 4      | 8      |
| `long long int` | 4      | 8      |
| `char *`        | 4      | 8      |
| `float`         | 4      | 4      |
| `double`        | 8      | 8      |

---

## Difference Between 32-bit & 64-bit OS


The core difference between these two types of OS is **word size**.

> **Word Size** → Word size means how much amount of data a processor could handle at one time.

---

## Chunks & Address Space


- It means sending data in the form of **chunks**.
- **32-bit OS** → It could address up to $2^{32}$ bytes
    - $2^{32}$ bytes = **4 GB** → So a 32-bit OS could use **4 GB of RAM** maximum.
- **64-bit** → $2^{64}$ → **~16 exabytes**

---

## Addressing & Byte Ordering

- In virtually almost all machines, a **multi-byte object** is stored in a **contiguous sequence** of memory.
- Suppose you have an `int` variable of type at address `0x100` in memory. So the address would be stored as:
    - `0x100`, `0x101`, `0x102`, `0x103`
    - → **4 bytes**

---

## Decimal to Binary Conversion

To convert decimal into binary, use the **divide by 2 method**:

1. Divide the number by 2 and record the remainders until you get the quotient 0.
2. Read remainders from **bottom to top**.

### Example: Converting 13 to Binary

| Operation | Quotient | Remainder | Index |
| --------- | -------- | --------- | ----- |
| 13 ÷ 2    | 6        | 1         | 3     |
| 6 ÷ 2     | 3        | 0         | 2     |
| 3 ÷ 2     | 1        | 1         | 1     |
| 1 ÷ 2     | 0        | 1         | 0     |

**Result:** `1101` → 13 in Binary ✓

---

## Hexadecimal & Nibble

- One **hexadecimal** digit is equal to **4 bits**
    - → **1 Nibble**