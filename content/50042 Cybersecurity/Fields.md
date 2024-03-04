# Fields
---
Informally, a field is a set of numbers in which we can add, subtract, multiply and divide (inverse). For example, real numbers, complex numbers. However, these are infinite sets, while in cryptography, we almost always need finite sets. 

## Definition
Fields are a subset of [[rings]], along with the additional properties:
- All elements of the field form an **additive group** with the operation + and the identity element 0
- All the elements of field except 0 form a **multiplicative** group with the operation * and the identity 1
- Distributivity law holds when two group operations are mixed

## Finite Fields
---
Also known as Galois fields, Finite fields only exist if there are p^m elements, where p refers to a prime and m refers to a positive integer

Example:
11 elements = GF(11) since $11^1$
256 elements = GF(256) since $2^8$ (better known as the [[AES]] Field)

Prime fields: when m = 1
Extension fields: when m > 1. GF($2^m$) are very important in cryptography

**Prime fields**
1. The elements of a prime fields GF(p) are ${0,1...p-1}$
2. The inverse a-1 must satisfy $a * a-1 = 1 mod p$

**Extension fields**
Made up of polynomials
- Elements of $GF(p^n)$ are coefficients of a polynomial of degree $n-1$
- The coefficients are in GF(p)
- Example: $GF(2^3) = {0, 1, x, x+1, x^2, x^2+1, x^2+x, x^2+x+1}$
- Characteristic of $GF(p^m) = p$

Addition and substitution:
Add coefficients of the same polynomials together, then modulo by 2
Note that add. and subtraction inf GF(2^m) are the same operations

Multiplication:
Intuition: Just do regular polynomial multiplication, then modulo by an irreducible "prime" polynomial

Irreducible polynomials
- An irreducible polynomial is a polynomial that cannot be factorized into factors with integer coefficients. Can use Factor Theorem to check if a polynomial is reducible
- For example, GF(2^3) = x^3 +x + 1. 
- For every Field GF(2^m), there are several irreducible polynomial. Therefore, each field must come with its stated irr. polynomial

Inversion:
- Use [[Extended Euclidean Algorithm|extended euclidean algorithm]] to solve. It can be computed on the fly 

## $GF(2^m)$ 
---
Given that p == 2;
- Addition is the same as XOR operation
- Multiplication is the same AND operation

#foc