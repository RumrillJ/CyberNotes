# Common Techniques to Data Representation

---

# Table of Contents
  - [Vocabulary](#vocabulary)
  - [Binary — Digital Values](#binary--digital-values)
  - [Octal](#octal)
  - [Hexadecimal](#hexadecimal)
  - [Converting Between Binary, Octal, and Hexadecimal](#converting-between-binary-octal-and-hexadecimal)
  - [Floating-Point Arithmetic](#floating-point-arithmetic)
    - [IEEE 754 Formats](#ieee-754-formats)
  - [Text, Audio, Image, and Video](#text-audio-image-and-video)
  - [Executables](#executables)
  - [Compression](#compression)
    - [Run-Length Encoding (RLE)](#run-length-encoding-rle)
    - [Compression Types](#compression-types)
  - [Check on Learning](#check-on-learning)


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

###  Shift Logical Left (`<<`)

 **left shift** moves all bits to the left and fills the empty rightmost bits with zeros.  
Each left shift multiplies the value by **2ⁿ**, where *n* is the number of positions shifted.

| Expression | Binary Before | Binary After | Decimal Before | Decimal After | Operation |
|-------------|----------------|---------------|----------------|---------------|------------|
| `0010 << 1` | 0010 | 0100 | 2 | 4 | × 2 |
| `0010 << 2` | 0010 | 1000 | 2 | 8 | × 4 |
| `0101 << 1` | 0101 | 1010 | 5 | 10 | × 2 |
| `0001 << 3` | 0001 | 1000 | 1 | 8 | × 8 |

---

###  Shift Logical Right (`>>`)

 **right shift** moves all bits to the right and fills the leftmost bits with zeros (for unsigned values).  
Each right shift divides the value by **2ⁿ**, where *n* is the number of positions shifted.

| Expression | Binary Before | Binary After | Decimal Before | Decimal After | Operation |
|-------------|----------------|---------------|----------------|---------------|------------|
| `1010 >> 1` | 1010 | 0101 | 10 | 5 | ÷ 2 |
| `1000 >> 2` | 1000 | 0010 | 8 | 2 | ÷ 4 |
| `1100 >> 3` | 1100 | 0001 | 12 | 1 | ÷ 8 |
| `0011 >> 1` | 0011 | 0001 | 3 | 1 | ÷ 2 |

>  Note: In signed integers, **arithmetic right shifts** may preserve the sign bit (1 for negative).

# Octal

**Octal** uses divisions of 8, and the result is the remainder in reverse order when converting from base 10 → base 8.

| Base^Place | 8⁴ | 8³ | 8² | 8¹ | 8⁰ |
|-------------|----|----|----|----|----|
| Place Value (Decimal) | 4096 | 512 | 64 | 8 | 1 |

---

## Octal to Decimal Examples

| Octal | Formula | Decimal |
|--------|----------|----------|
| 24₈ | (2 × 8¹) + (4 × 8⁰) | **20** |
| 457₈ | (4 × 64) + (5 × 8) + (7 × 1) | **303** |
| 357₈ | (3 × 64) + (5 × 8) + (7 × 1) | **239** |

---

## Decimal to Octal Examples

| Decimal | Conversion | Octal |
|----------|-------------|--------|
| 98 | (64 × 1) + (8 × 4) + 2 | **142₈** |
| 121 | (64 × 1) + (8 × 7) + 1 | **171₈** |
| 128 | (64 × 2) | **200₈** |

---

## Example: Add 171₈ + 246₈
| Column | Calculation (Base 8) | Carry | Result Digit |
|---------|----------------------|--------|----------------|
| **Ones** | 1 + 6 = **7** | 0 | 7 |
| **Eights** | 7 + 4 = **13 (₈)** → 1 carry, 3 write down | 1 | 3 |
| **Sixty-fours** | 1 + 2 + 1(carry) = **4** | 0 | 4 |

**437₈**

### Example: Add 765₈ + 167₈

| Column | Addition | Decimal Sum | Convert to Octal | Write Down | Carry |
|:-------:|:----------:|:--------------:|:----------------:|:------------:|:-------:|
| Ones | 5 + 7 | 12 | 12₁₀ = 14₈ | 4 | 1 |
| Eights | 6 + 6 + 1(carry) | 13 | 13₁₀ = 15₈ | 5 | 1 |
| Sixty-fours | 7 + 1 + 1(carry) | 9 | 9₁₀ = 11₈ | 1 | 1 |

**Carry the last 1 = 1154₈**


# Hexadecimal

**Hexadecimal** employs a system of 16 symbols — digits **0–9** and characters **A–F**.

| Symbol | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F |
|---------|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Value   | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |

Hexadecimal numbers use **powers of 16**, whereas binary uses **powers of 2**.

---

## Hex to Decimal Examples

| Hex | Breakdown | Decimal |
|------|------------|----------|
| D1CE₁₆ | (13 × 4096) + (1 × 256) + (12 × 16) + (14 × 1) | **53710₁₀** |
| BE₁₆ | (11 × 16) + (14 × 1) | **190₁₀** |


Decimal to Hex examples: 
(You can compute these using repeated division by 16 and recording remainders.)

# Hexadecimal Addition 
4A + 5C 

A + C = 10 + 13 = 23 = 16_16 = 6 Carry the 1 
4 +(1 carried over) + 5  = 10 = A 
= A6 

# Hexadecimal Subtraction 
5A - 3B 
A - B = (10 - 11) -> Borrow 1 from 5 -> (26 - 11) = 15 
5 (-1 carried over) - 3 = 1 
15 = F in Hex
1F 

# Converting Between Binary, Octal, and Hexadecimal

Binary, Octal, and Hexadecimal are all **powers of 2**:

| Base | Powers of | Example Range |
|-------|------------|----------------|
| Base 16 | 16⁰ → 16³ | 1 Hex Digit = 4 Bits |
| Base 8 | 8⁰ → 8⁴ | 1 Octal Digit = 3 Bits |
| Base 2 | 2⁰ → 2¹² | Binary Representation |

| Place (Decimal) | 4096 | 2048 | 1024 | 512 | 256 | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

---

## Hex to Octal Conversion Example

**Convert:** `1FB9₁₆`

| Hex | Binary Equivalent |
|------|--------------------|
| 1 | 0001 |
| F (15) | 1111 |
| B (11) | 1011 |
| 9 | 1001 |

Combine → `0001 1111 1011 1001`  
Group into 3-bit sections (for Octal):  
`000 111 110 111 001` → **017671₈**

## Example: Convert 574₈ to Binary
| Octal Digit | Binary Equivalent |
|--------------|-------------------|
| 5 | 101 |
| 7 | 111 |
| 4 | 100 |

## Example: Convert 0001 0111 1100₂ to Hexadecimal
| Binary | Hex |
|---------|-----|
| 0001 | 1 |
| 0111 | 7 |
| 1100 | C |


# Floating-Point Arithmetic

Numbers like **123.75** are real numbers. Computers represent these using **floating-point numbers**.

**IEEE 754 Standard** defines this storage using **scientific notation**:

| Component | Description |
|------------|--------------|
| **Sign Bit** | 0 for positive, 1 for negative |
| **Exponent** | Represents power of 2 |
| **Mantissa** | Fractional part after the decimal |

Floating-point numbers provide a **trade-off between range and precision**, enabling representation of extremely small or large values.

### IEEE 754 Formats

| Precision | Total Bits | Sign | Exponent | Mantissa |
|------------|-------------|------|-----------|-----------|
| 32-bit (Single) | 32 | 1 | 8 | 23 |
| 64-bit (Double) | 64 | 1 | 11 | 52 |

---

# Text, Audio, Image, and Video

File extensions and formats define **how data is encoded**.

- All files are made of bits (1s and 0s).
- File formats interpret those bits into meaningful forms (text, image, audio, etc.).
- **Abstraction** — simplifying data representation for easier processing.

---

## Text

- Text files use **ASCII** (American Standard Code for Information Interchange).  
- **Extended ASCII** uses 8 bits → 256 characters/symbols.  
- Each character maps to a unique binary value.

---

## Audio

- **Analog Signal**: Continuous wave with infinite possible values.
- Sound waves are analog signals; digital systems sample and quantize them.

---

## Image

- An **image** is made up of **pixels**.
- Each pixel uses 3 × 8-bit color values (for **RGB**: Red, Green, Blue).
- **Example:**
  - Red in Hex: `#FF0000`
  - Red in Binary: `11111111 00000000 00000000`
    - R = 255, G = 0, B = 0

---

# Video

The **video** process involves streaming images over frames per second (**FPS** or *Frame Rate*).  
A rapid succession of images creates the illusion of **motion**.

### Common Frame Rates
- **25 FPS** – Standard for Film  
- **25 or 30 FPS** – Common for Digital Video  
- **30 FPS** – Standard Broadcast Rate  

---

## File Examples

| Type | Example File Formats |
|------|------------------------|
| **Text** | `.pdf`, `.rtf` |
| **Audio** | `.mp3`, `.wav` |
| **Image** | `.png`, `.bmp` |
| **Video** | `.avi`, `.mpeg` |

---

# Executables

An **executable** is a series of instructions that a computer can perform directly.  
Humans can read **source code**, but not executable machine code.

To transform a source file into an executable file, it must pass through a **compiler** or **assembler**.

| Tool | Description |
|------|--------------|
| **Compiler** | Translates source code from a high-level programming language into machine language to create an executable program. |
| **Assembler** | Converts assembly code to machine code, checks for syntax and logic errors, and performs diagnostics. |

---

# Compression

**Compression** reduces the size of data files so they can be stored or transmitted more efficiently.

### Run-Length Encoding (RLE)
RLE is a **lossless compression** method that represents consecutive repeated values (runs) as a single value and count.

AAAAAAAAAAbbbbbbbbbbbbbCccccDDDDDDDDD (37 Characters/37 Bytes)
AADb1C4C9D(10 Bytes) - utilizes base 16 (Hexadecimal) 

Example:
ABBAAB (6 Characters / 6 Bytes)
1A2B2A1B (8 Bytes) 

## Compression Types

- **Lossless Compression**  
  Reduces file size **without losing quality** — data can be fully restored to its original form.

- **Lossy Compression**  
  Allows for **variable quality levels** by decreasing file size.  
  At higher levels of compression, **deterioration becomes noticeable**.

---

## Check on Learning

**1. What would the signed byte `1111 1010` be converted to in decimal?**  
→ Swap binary: `0000 0101 = 5`, then +1 = **-6**

---

**2. What is the hexadecimal `A6` in decimal (base 10)?**  
→ (10 × 16) + (6 × 1) = **166**

---

**3. What is base 8 called?**  
→ **Octal**

---

**4. What is base 16 called?**  
→ **Hexadecimal**

---

**5. In signed arithmetic, what does the leftmost number represent?**  
→ **Sign of the number**

---

**6. What arithmetic uses formulaic representation of real numbers as an approximation?**  
→ **Floating-Point Arithmetic**

---

**7. Text files are composed of data in what language?**  
→ **ASCII**

---

**8. What translates source code from a high-level programming language to machine-level language?**  
→ **Compiler**

---

**9. What is `AAbbCCCdD` after performing Run-Length Encoding (RLE)?**  
→ **2A2b3C1d1D**

---

**End of Notes**



		







  












