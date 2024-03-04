# Diffie-Hellman Key Exchange
---
## Settings
---
Public parameters: Large prime $p$ and some integer base $g$


Steps to perform DHKE
1. Each creates a random private number (a for alice, b for bob)
2. Compute $A = g^a mod p$  and $B = g^b modp$
3. Share A and B with each other
4. Compute $A^b = g^{ab}  modp$ and $B^{a} = g^{ba}modp$

Why is DHKE secure?
Relies on [[Discrete Log Problem]] as a one way function: it is easy to calculate the remainder, but hard to work out the initial parameters given the result

How can we speed up the calculation of the remainder?
Use the square and multiply method (convert power into binary)
Repeatedly taking the modulo of the incremental powers
#foc