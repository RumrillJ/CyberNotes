# Common Techniques to Data Representation

---

##  Vocabulary

| Term | Description |
|------|--------------|
| **Positional Number** | A system for establishing how numeric values are represented (left → right by significance). |
| **Base** | The simplest structure of a number system. |

---

##  Binary — Digital Values

| Unit | Bits | Equivalent | Notes |
|------|------|-------------|--------|
| **Bit** | 1 | — | Binary Digit |
| **Nibble** | 4 | 0.5 Byte | Half a byte |
| **Byte** | 8 | 1 Byte | Basic storage unit |
| **Word (W)** | 16 | 2 Bytes | 1 Word |
| **Double Word (DW)** | 32 | 4 Bytes / 2 Words | 1 Double Word |
| **Quad Word (QW)** | 64 | 8 Bytes / 4 Words / 2 DWords | 1 Quad Word |

---

## Binary Number Examples

Binary values can be **signed (+ / -)**.

### Example — Number 36
| Bit Values | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-------------|------|----|----|----|---|---|---|---|
| Binary      | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 |

**Binary:** `00100100`

---

### Example — Number 42
| Bit Values | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-------------|------|----|----|----|---|---|---|---|
| Binary      | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 0 |

**Binary:** `00101010`

---

## ➖ Negative Binary Values

Signed integers use **Two’s Complement** representation to handle positive and negative numbers.

###  Example: 5 + (-3) = 2

```text
Step 1: Represent 5 and 3 in binary
5  → 0000 0101
3  → 0000 0011

Step 2: Convert +3 to -3
Flip all bits (invert)
3 → 0000 0011 → 1111 1100

Add 1 to the inverted bits:
1111 1100 + 1 = 1111 1101  (this is -3)

Step 3: Add 5 and -3
   0000 0101
+  1111 1101
-----------------
1 0000 0010

Step 4: Drop the overflow (leftmost 1)
Result → 0000 0010 = 2
```

# Binary Shifters

## Binary Shifters

Binary **shifting** is an operation that moves bits left or right.  
Each shift changes the binary value by a power of two.

---

###  Left Shift (`<<`)

A **left shift** moves all bits to the left and fills the empty rightmost bits with zeros.  
Each left shift multiplies the value by **2ⁿ**, where *n* is the number of positions shifted.

| Expression | Binary Before | Binary After | Decimal Before | Decimal After | Operation |
|-------------|----------------|---------------|----------------|---------------|------------|
| `0010 << 1` | 0010 | 0100 | 2 | 4 | × 2 |
| `0010 << 2` | 0010 | 1000 | 2 | 8 | × 4 |
| `0101 << 1` | 0101 | 1010 | 5 | 10 | × 2 |
| `0001 << 3` | 0001 | 1000 | 1 | 8 | × 8 |

---

###  Right Shift (`>>`)

A **right shift** moves all bits to the right and fills the leftmost bits with zeros (for unsigned values).  
Each right shift divides the value by **2ⁿ**, where *n* is the number of positions shifted.

| Expression | Binary Before | Binary After | Decimal Before | Decimal After | Operation |
|-------------|----------------|---------------|----------------|---------------|------------|
| `1010 >> 1` | 1010 | 0101 | 10 | 5 | ÷ 2 |
| `1000 >> 2` | 1000 | 0010 | 8 | 2 | ÷ 4 |
| `1100 >> 3` | 1100 | 0001 | 12 | 1 | ÷ 8 |
| `0011 >> 1` | 0011 | 0001 | 3 | 1 | ÷ 2 |

> ⚙️ Note: In signed integers, **arithmetic right shifts** may preserve the sign bit (1 for negative).

**End of Notes**








		







  












