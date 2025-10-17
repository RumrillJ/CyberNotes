**Common Techniques to Data Representation:**


	Vocab: 
		Positional number - A system for establishing how numeric values are represented (Left -> Right from significance) 
		Base - Simplest structure of a number system 

	
	Binary - Digital Values
		Bit - 1 Binary Digit
		Nibble - 4 bits || 0.5 Byte
		Byte - 8 Bits || 1 Byte
		Word - 16 Bits || 2 Bytes
		DW - 32 Bits || 4 Bytes || 2 W
		QW - 64 Bits || 8 Bytes || 4 W || 2 DW

Binary Samples (Binary values can be signed (+ / -) 
num36 
128 64 32 16 8 4 2 1
	1	1
0100100

num 42
128 64 32 16 8 4 2 1 
0    0	1 0  1 0 1 0 

0010 
Negative Binary Val 
Signed integers -> (+ / -) 

"Order of Magnitude" = Scientific Notation 	
				
**Binary Subtraction instructions**

	5 + (-3) = 2
	5 : 00000101
	3:  00000011
	-3(flip), then add 1 -> 1111 1101
	---------------------------------
	if (total > 1) -> carry pointer left
	Result: 1 0000 0011


**Binary Fractional Values:**

	8 4 2 1 .5 .25 .125 0.0625
		Ex: 10.5 : 1010.1 
		Ex: 10.25 : 1010.01

**Shifters**

	Left Shift:
		0010 << 1 = 0100 
		0010 << 2 = 1000 

	Right Shift:
		0010 >> 1 = 0001
		1011 >> 2 = 0010 






		







  










