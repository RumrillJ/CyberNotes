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

**Octal** uses divisions of 8 and the result is the remainder in reverse order from base 10 -> base 8. 
|Base^Place | 8^4 | 8^3 | 8^2 | 8^1 | 8^0 | 
|-------------|----------------|---------------|----------------|---------------|---------------|
|Place value in Decimal| 4096 | 512 | 64 | 8 | 1 | 

Octal to Decimal Examples:
24_8 -> (2 * 8^1) + (4 * 8^0) = 20
457_8 -> (64* 4) + (8 * 5) + (7 * 1) = 303
357_8 -> (64 * 3) + (8 * 5) + (7 * 1) = 239

Decimal to Octal Examples:
98 -> (64 * 1) + (8 * 4) + 2 = 142_8
121 -> (64 * 1) (8 * 7) + 1 = 171_8 
128 -? (64 * 2) = 200_8

Octal Addition Example: 
171 + 246 = 437_8 
1 7 1 
2 4 6
------
4 3 7

765 + 167 = 1154_8 
1 7^1 6^1 5 
  1 6 7
----------
1 1 5 4

# Hexadecimal
**Hexadecimal** employs a system of 16 digits containing numbers (0 - 9) and characters (A to F)
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15| 
Hex uses **power of 16**, compared to binary that uses powers of 2

Hex to Decimal examples: 
**D1CE_16**
D = 13 * 4096
1 = 1 * 256
C = 12 * 16
E = 14 * 1
53710_10

**BE_16 **
11 * 16
14 * 1 
190_10 

Decimal to Hex examples: 

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

# Converting between Binary, Octal, and Hexadecimal 
Binary, Octal, and Hexadecimal are all powers of 2: 

| Base 16 | 16 ^ 3 |---|---|---|16^2|---|---|---|16^1|---|---|---|16^0|
| Base 8 | 8 ^ 4 |---|---|8^3|---|---|8^2|---|---|8^1|---|---| 8^0|
| Base 2 | 2^12 | 2^11 | 2^10 | 2^9 | 2^8 | 2^7 | 2^6| 2^5 | 2^4 | 2^3 | 2^2 | 2^1 | 2^0 |
|Place Value in decimal|4096|2048|1024|512|256|128|64|32|16|8|4|2|1|
Each octal digit = 3 bits
Each hexadecimal dgit = 4 bits 

# Hex to Octal Conversion Examples (Octal can only hold 3 bits) 
1FB9 
1 = 0001
F(15) = 1111 
B(11) = 1011 
9 = 1001
0 001 111 101 111 001
0  1  7   6    7   1 

# Octal to Hex 
574_8
to Binary
5    7   4
000 101 111 100

to Hex 
0001 0111 1100
1      7   C_16  


# Floating-Point Artihmetic
Number 123.75 is a real number, computers process and store this number as a **Floating Point Number**. 
IEEE 754 defines how floating-point numbers are stored in scientific notation
- Sign Bit (0 if value is positive (+) and 1 if negative(-)
- Exponent
- Mantissa (stores bit of the significant located after the decimal point
  
-Represents real numbers as an approximation to support trade off between range and precision
-Often used in systems with very small and very large real numbers for faster processing times 

Two most common IEEE 754 floating point standard supports 32 Bit single precision and 64 Bit double precision
32 Bits -> Sign(1 Bit) | Exponent (8 Bits) | Mantissa (23 Bits)
64 Bits -> Sign(1 Bit) | Exponent (11 Bits) | Mantissa (52 Bits) 

# Text, Audio, Image, and Video 
File extensions & formats are standard forms of encoding data within a file 
Files have characteristics dependent on Software
Encoded information is just 1's and 0's in abstract forms
	-abstraction: identifying simpler components in an abstract format
File formatting is done by representing bits as Hex values which are interpreted by the program to produce an output or px in img


# Text 
Text files are composed of data in ASCII (American Standard Code for Information Exchange) 
Extended ASCII uses 8 bits representing 256 Characters/Symbols 
Each character in ASCII table represents binary value 

# Audio
Analog signal is continuous wave with potential for infinite resolution.
Anything that makes noise product Analog Signals (Sound Wave)

# Image
Image is comprised of pixels
3 8-bit color values for RGB(Red, Green, Blue)
Colors referred to a combination of 6 Hex Symbols 
Red color in Hex (FF 00 00) (Red, 0 Green, 0 Blue) 
Red color in Binary 11111111 00000000 00000000 
						R        G        B 

# Video 
Process of streaming images over frames per seconds (FPS (Frame Rate))
Rapid Sucession of images create "Motion" 
Common FPS
25 for Film
25 or 30 for Digital Video
30 for Standard Broadcast 


**File Examples**
Examples of Text: pdf, rtf
Examples of Audio: mp3, wav
Examples of Image: png, bmp
Examples of Video: avi, mpeg 

# Executables 
**Executable** is a series of instructions a computer directly performed 
(Humans can't read executable code, but can read source code)

To transform src file into exe file -> pass through compiler or assembler

|Compiler | translates src code from a high-level programming language to machine language to create executable program|
|---|---| 
|Assembler| takes assembly code and conver to machine code (checks instructions for syntax and/or logic errors and conducts diagnosis for errors | 

# Compression 
**Compression** allows reduction in data size o a file to be stored/transmitted efficiently
(RLE) Run-Length Encoding is a method of data compression, when a run is a repeated occurence of the same value.
AAAAAAAAAAbbbbbbbbbbbbbCccccDDDDDDDDD (37 Characters/37 Bytes)
AADb1C4C9D(10 Bytes) - utilizes base 16 (Hexadecimal) 

Example:
ABBAAB (6 Characters / 6 Bytes)
1A2B2A1B (8 Bytes) 

Lossless Compression - Reduces file size without losing quality 
Lossy Compression - Allows for variable quality levels by decreasing file size. At higher levels of compression, deterioration becomes noticable. 

# Check on Learning
What would the signed byte 1111 1010 be converted to decimal? 
*Swap binary = 0000 0101 = 5, then + 1 = -6 

What is the hexadecimal A6 in Decimal (base 10)? (10 * 16) + (6 * 1) = 166

What is base 8 called? Octal

What is base 16 called? Hexadecimal 

In signed artithmetic what does the leftmost number represent? Sign of a number 

What arithmetic uses formulaic representation of real numbers as an approximation? Floating-Point Arithmetic

Text files are composed of data in what language? ASCII

What translates source code from a high-level programming language to a machine level language? Compiler 

What is AAbbCCCdD after performing RLE? 2A2b3C1d1D

**End of Notes**








		







  












