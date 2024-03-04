# Advanced Encryption System
---
Also known as Rijndael, AES is the most popular block cipher algorithm in use right now

For AES:
Constants are binary in $GF(2^m)$ (where m = 8 in AES)
Elements are represented as a 2-bit value, eg 01, 100, instead of $x^3$
$GF(2^8)$ used for the S-box and MixColumns in AES
The "AES irreducible polynomial" = x^8 + x^4 + x^3 + x + 1


AES is not a fiestel network cipher. 
For an overall detailed structure of the AES, see Fig 4.2
For a detailed structure of each round of AES, see Fig 4.3
Each round consists of 4 layers:
1. Byte Substitution (or "S-Box layer", to provide Confusion)
	- All 16 S-boxes (1 for each byte) are the same
1. ShiftRow (provide [[Diffusion]])
	- Similar to permutation
2. MixColumn (provide [[Diffusion]])
3. KeyAddition

AES will carry out 9 rounds, but last round doesnt have the MixCol layer
Key Whitening is done at the start and the end of AES

## S-Box table
**Construction**
Consider a byte entry as a polynomial in $GF(x^8)$ and compute its inverse
Take the inverse and do an affine mapping, which is basically matrix multiplication with a fixed matrix, addition with another fixed vector and mod of 2
#foc