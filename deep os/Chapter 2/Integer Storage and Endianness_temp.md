
## Byte-Addressable Memory
In modern systems, memory is **byte-addressable**. This means the smallest unit of memory that has its own unique address is a **byte** (8 bits). 

> [!note]
> Even if you have a 4-byte (32-bit) integer, it occupies four contiguous addresses. Each address points to exactly one 8-bit byte.

| Address  | Data (8 bits) |
| :------- | :------------ |
| `0x1000` | `01001011`    |
| `0x1001` | `11100001`    |
| `0x1002` | `00000000`    |

---

## Decimal to Binary Conversion
To convert a decimal number to binary, use the **division-by-2 method**. Divide the number by 2 and record the remainder. Repeat until the quotient is 0. Read remainders from bottom to top.

**Example: Convert 13 to Binary**
1. 13 ÷ 2 = 6, remainder **1** (LSB)
2. 6 ÷ 2 = 3, remainder **0**
3. 3 ÷ 2 = 1, remainder **1**
4. 1 ÷ 2 = 0, remainder **1** (MSB)

**Result:** `1101₂`

> [!warning] The BCD Trap
> A common mistake is converting each decimal digit separately.
> - **Wrong:** 13 -> `1` (0001) and `3` (0011) -> `00010011` (This is Binary Coded Decimal, used in niche cases but NOT how integers are stored).
> - **Right:** 13 -> `1101` (The value as a whole).

---

## Binary to Hexadecimal Conversion
Hexadecimal (Base 16) is a shorthand for binary. Since $2^4 = 16$, one hex digit represents exactly **4 bits** (a nibble).

| Binary | Hex | Binary | Hex |
| :----- | :-- | :----- | :-- |
| 0000   | 0   | 1000   | 8   |
| 0001   | 1   | 1001   | 9   |
| 0010   | 2   | 1010   | A   |
| 0011   | 3   | 1011   | B   |
| 0100   | 4   | 1100   | C   |
| 0101   | 5   | 1101   | D   |
| 0110   | 6   | 1110   | E   |
| 0111   | 7   | 1111   | F   |

**Example:** `11010110₂`
1. Group: `1101` | `0110`
2. Convert: `D` | `6`
3. **Result:** `0xD6`

---

## Decimal to Hexadecimal Conversion
Use the **division-by-16 method**.

**Example: Convert 1342 to Hex**
1. 1342 ÷ 16 = 83, remainder **14** (`E`)
2. 83 ÷ 16 = 5, remainder **3** (`3`)
3. 5 ÷ 16 = 0, remainder **5** (`5`)

**Result:** `0x53E`

---

## Endianness: Little-Endian vs. Big-Endian
Multi-byte objects (like a 4-byte `int`) must be stored in a specific byte order.

- **Big-Endian:** Most Significant Byte (MSB) is stored at the smallest address. (Human readable: `0x12345678` stays `12 34 56 78`).
- **Little-Endian:** Least Significant Byte (LSB) is stored at the smallest address. (**x86-64 standard**).

> [!tip]
> Think "Little End = First Address".

---

## Full Worked Example: `int x = 1342`
Assuming a 4-byte (32-bit) integer on an **x86-64 (Little-Endian)** system.

### 1. Convert Decimal to Hex
From previous step: `1342₁₀ = 0x53E`.

### 2. Pad to Variable Size (4 bytes)
`0x0000053E`

### 3. Identify Bytes
- Byte 0 (LSB): `0x3E`
- Byte 1: `0x05`
- Byte 2: `0x00`
- Byte 3 (MSB): `0x00`

### 4. Layout in Memory (Little-Endian)
Starting at address `0x2000`:

| Address | Value (Hex) | Byte Significance |
| :--- | :--- | :--- |
| `0x2000` | `3E` | LSB |
| `0x2001` | `05` | |
| `0x2002` | `00` | |
| `0x2003` | `00` | MSB |

---

## CPU Reassembly
When the CPU executes an instruction like `MOV EAX, [0x2000]`, it knows the size of the operand (4 bytes for EAX).

1. It fetches 4 bytes starting at `0x2000`.
2. Because it is a Little-Endian processor, it shifts the bytes into the register in reverse order:
   - Byte at `0x2000` (`3E`) goes to bits 0-7.
   - Byte at `0x2001` (`05`) goes to bits 8-15.
   - Byte at `0x2002` (`00`) goes to bits 16-23.
   - Byte at `0x2003` (`00`) goes to bits 24-31.
3. The register value becomes `0x0000053E`, which equals `1342`.
